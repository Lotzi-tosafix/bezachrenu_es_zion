# טיימר חורבן בית המקדש (Temple Destruction Timer)

פרויקט זה הוא ווידג'ט פשוט המציג טיימר דינמי הסופר את הזמן שחלף מאז חורבן בית המקדש השני.

הווידג'ט זמין בשתי שפות (עברית ואנגלית), קל להטמעה בכל אתר אינטרנט באמצעות `<iframe>`, והוא כולו לחיץ ומפנה את המשתמש לדף הטיימר באתר Tosafix.

## תצוגה מקדימה

![תצוגה מקדימה של הטיימר](https://github.com/user-attachments/assets/7513e6dc-57d8-46d5-977a-63b3041190eb)

## הדגמה חיה

*   **[קישור לגרסה בעברית](https://lotzi-tosafix.github.io/bezachrenu_es_zion/timer-he.html)**
*   **[קישור לגרסה באנגלית](https://lotzi-tosafix.github.io/bezachrenu_es_zion/timer-en.html)**

## איך להטמיע באתר שלכם

אנו מציעים שתי דרכים להטמיע את הטיימר באתרכם. הדרך האוטומטית מומלצת לחווית המשתמש הטובה ביותר.

---

### **1. הטמעה אוטומטית לפי שפת הדפדפן (מומלץ)**

שיטה זו תציג באופן אוטומטי את הגרסה העברית לגולשים שהדפדפן שלהם מוגדר לעברית, ואת הגרסה האנגלית לכל השאר.

**שלב 1:** הדביקו את ה-`<div>` הבא במקום המדויק בעמוד בו תרצו שהטיימר יופיע:
```html
<div id="temple-timer-container"></div>
```

**שלב 2:** הדביקו את קטע ה-`<script>` הבא ממש לפני סגירת תגית ה-`</body>` בעמוד שלכם:
```html
<script>
    (function() {
        // --- הגדרות ---
        const hebrewUrl = 'https://lotzi-tosafix.github.io/bezachrenu_es_zion/timer-he.html';
        const englishUrl = 'https://lotzi-tosafix.github.io/bezachrenu_es_zion/timer-en.html';
        const containerId = 'temple-timer-container';
        
        // --- לוגיקת זיהוי שפה ויצירת האייפרם ---
        const userLang = navigator.language || navigator.userLanguage; 
        const isHebrew = userLang.toLowerCase().startsWith('he');
        
        const iframeUrl = isHebrew ? hebrewUrl : englishUrl;
        const title = isHebrew ? 'טיימר חורבן בית המקדש' : 'Beit HaMikdash Destruction Timer';
        
        const iframe = document.createElement('iframe');
        iframe.setAttribute('src', iframeUrl);
        iframe.setAttribute('width', '330');
        iframe.setAttribute('height', '215');
        iframe.setAttribute('title', title);
        iframe.style.border = 'none';
        iframe.style.overflow = 'hidden';
        
        const container = document.getElementById(containerId);
        if (container) {
            container.appendChild(iframe);
        } else {
            console.error('Temple Timer container with ID "' + containerId + '" was not found.');
        }
    })();
</script>
```

---

### **2. הטמעה ידנית (גרסה יחידה)**

אם אתם מעדיפים לקבוע גרסה ספציפית שתמיד תוצג, השתמשו באחד מהקודים הבאים.

#### **גרסה בעברית**
```html
<iframe src="https://lotzi-tosafix.github.io/bezachrenu_es_zion/timer-he.html" width="330" height="215" style="border:none; overflow:hidden;" title="טיימר חורבן בית המקדש"></iframe>
```

#### **גרסה באנגלית (English Version)**
```html
<iframe src="https://lotzi-tosafix.github.io/bezachrenu_es_zion/timer-en.html" width="330" height="215" style="border:none; overflow:hidden;" title="Beit HaMikdash Destruction Timer"></iframe>
```

---

### התאמה אישית

ניתן לשנות את הגודל של חלונית הטיימר על ידי שינוי הערכים `width` (רוחב) ו-`height` (גובה) בקוד ה-iframe, כדי להתאים אותו באופן מושלם לעיצוב האתר שלכם.

## קרדיטים

הטיימר משתמש בספריית ה-JavaScript [SecondTempleTimerLibrary](https://github.com/kdroidFilter/SecondTempleTimerLibrary) לחישוב הזמן.

## רישיון

פרויקט זה מופץ תחת רישיון MIT.
