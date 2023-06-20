# **Анализ открытия сайта с использованием Chrome DevTools**
## **1. Network*

### **_1.1 Профиль загрузки ресурсов при открытии страницы_**

[HAR архив](./Network/www.gd.ru.har)

### **_1.2 Неоптимальные места_**

**_1.2.1 Дублирование ресурсов_**

- 1cont.ru

![](./Network/01-resourceDuplication/1cont.png)

- bootstrap.bundle.min.js, bootstrap.min.css, bootstrap.min.js

![](./Network/01-resourceDuplication/bootstrapDublicates.png)

- cast_sender.js

![](./Network/01-resourceDuplication/cast_sender.png)

- code.js

![](./Network/01-resourceDuplication/code.js.png)

- data:image/png;base...

![](./Network/01-resourceDuplication/data_image_png_base.png)
![](./Network/01-resourceDuplication/data_img_png_base.png)

- fontawesome-webfont.woff2?v=4.7.0

![](./Network/01-resourceDuplication/fontawesome-webfont.woff2%3Fv%3D4.7.0.jpg)

- jquery-3.5.1.js

![](./Network/01-resourceDuplication/jquery-3.5.1.js.png)

- popper.min.js

![](./Network/01-resourceDuplication/popper.min.js.png)

- system_gd-logo

![](./Network/01-resourceDuplication/system_gd-logo.png)

- user-recognition

![](./Network/01-resourceDuplication/user-recognition.png)

**_1.2.2 Лишний размер ресурса_**

- JS файлы с большим весом

base.js: 767kB - transferred over network, 2.4MB - resource size
common.js: 389kB - transferred over network, 1.4MB - resource size
community.js: 383kB - transferred over network, 1.4MB - resource size

![](./Network/02-resourceUnnecessarySize/js_unnecessaryZize.png)

- Шрифты с большим весом

![](./Network/02-resourceUnnecessarySize/font_unnecessarySize.png)

- CSS файлы с большим весом

fonts.css: 255kB - transferred over network, 339kB - resource size

![](./Network/02-resourceUnnecessarySize/css_unnecessarySize.png)

- IMG файлы с большим весом

![](./Network/02-resourceUnnecessarySize/01-img_unnecessarySize.png)
![](./Network/02-resourceUnnecessarySize/02-img_unnecessarySize.png)

**_1.2.3 Медленно загружающиеся ресурсы_**

Были выбраны запросы с длительностью > 200ms

![](./Network/03-resourcesSlowLoading/01-slowLoading.png)
![](./Network/03-resourcesSlowLoading/02-slowLoading.png)
![](./Network/03-resourcesSlowLoading/03-slowLoading.png)
![](./Network/03-resourcesSlowLoading/04-slowLoading.png)

**_1.2.4 Ресурсы, блокирующие загрузку_**

Были выбраны запросы, начало которых произошло до этапа загрузки страницы First Paint

![](./Network/04-resourcesBlockingDownloads/blockingDownloads.png)

**_1.2.5 Что-то еще_**

- Заблокированные запросы
  ![](./Network/05-somethingElse/blockedRequests/01-blocked.png)
  ![](./Network/05-somethingElse/blockedRequests/02-blocked.png)
  ![](./Network/05-somethingElse/blockedRequests/03-blocked.png)

- Запросы со статусом 302, которые привели к лишним запросам по новым адресам
  ![](./Network/05-somethingElse/status302Requests/status302.png)

## **2. Performance**

### **_2.1 Профиль загрузки страницы_**

[Profile.json](./Performance/Profile.json)

### **_2.2 Время от начала навигации до событий:_**

- **First Paint - 577.2 ms**

![](./Performance/screenShots/FirstPaint.png)

- **First Contentful Paint - 577.2 ms**

![](./Performance/screenShots/FirstContentfulPaint.png)

- **Largest Contentful Paint - 758.9 ms**

![](./Performance/screenShots/LargestContentfulPaint.png)

- **DOMContentLoaded Event - 2.0 s**
- **Event - 2.79 s**

![](./Performance/screenShots/DCL_Load.png)

### **_2.3 DOM-элемент, на котором происходит LCP_**

![](./Performance/screenShots/LCP_dom-element.png)

### **_2.4 Времени, которое тратится на разные этапы обработки документа_**

- **Loading - 34 ms**
- **Scripting - 266 ms**
- **Rendering - 156 ms**
- **Painting - 15 ms**

![](./Performance/screenShots/summary.png)

## **3. Coverage**

### **_3.1 Скриншот вкладки после загрузки страницы_**

![](./Coverage/Coverage.png)

### **_3.2 Объём неиспользованного CSS в ходе загрузки страницы в килобайтах_**

- **Unused CSS - 564 kB**

![](./Coverage/unused_CSS.png)

### **_3.3 Объём неиспользованного JS в ходе загрузки страницы в килобайтах_**

- **Unused JS - 2.3 MB**

![](./Coverage/unused_JS.png)

# **Анализ при замедлении CPU 4x slowdown и эмуляции сети Slow 3G**

## **1. Network**

### **_1.1 Профиль загрузки ресурсов при открытии страницы_**

[HAR архив](./SlowNetwork/www.gd.ru-slow.har)

### **_1.2 Неоптимальные места_**

Всё тоже самое, что и при первом тесте, только дольше.

![](./SlowNetwork/network-slow.png)

## **2. Performance**

### **_2.1 Профиль загрузки страницы_**

[Profile-slow.json](./SlowNetwork/Profile-slow.json)

### **_2.2 Время от начала навигации до событий:_**

- **First Paint - 9460.1 ms**

![](./SlowNetwork/fp-slow.png)

- **First Contentful Paint - 9460.1 ms**

![](./SlowNetwork/fcp-slow.png)

- **Largest Contentful Paint - 12632.9 ms**

![](./SlowNetwork/lcp-slow.png)

- **DOMContentLoaded Event - 27162.9 ms**

![](./SlowNetwork/domload-slow.png)

- **Event - 51.55 s**

![](./SlowNetwork/load-slow.png)

### **_2.3 DOM-элемент, на котором происходит LCP_**

![](./SlowNetwork/lcp-element.png)

### **_2.4 Времени, которое тратится на разные этапы обработки документа_**

- **Loading - 366 ms**
- **Scripting - 13244 ms**
- **Rendering - 4718 ms**
- **Painting - 739 ms**

![](./SlowNetwork/summary-slow.png)

## **3. Coverage**

Всё то же самое, что и при первом тесте

![](./SlowNetwork/coverage-slow.png)
