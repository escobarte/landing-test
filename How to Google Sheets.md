# Google Sheets Integration
## Step 1 — Create Google Sheet
Go to sheets.google.com
Create new sheet, name it: Transnatur Leads
Add headers in Row 1:
A: Timestamp | B: First Name | C: Last Name | D: Phone | E: Email | F: CDL Class | G: Experience | H: State

## Step 2 — Create Apps Script
In the Sheet: click Extensions → Apps Script
Delete all existing code
Paste this code:
function doPost(e) {
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();
  var data = JSON.parse(e.postData.contents);
  
  sheet.appendRow([
    new Date(),
    data.firstName,
    data.lastName,
    data.phone,
    data.email,
    data.cdlClass,
    data.experience,
    data.state
  ]);
  
  return ContentService
    .createTextOutput(JSON.stringify({ result: "success" }))
    .setMimeType(ContentService.MimeType.JSON);
}
Click Deploy → New Deployment
Type: Web app
Execute as: Me
Who has access: Anyone
Click Deploy → Copy the Web App URL
## Step 3 — Add URL to Form
In form.html, replace YOUR_APPS_SCRIPT_URL with the copied URL:

const GOOGLE_SHEET_URL = "https://script.google.com/macros/s/YOUR_APPS_SCRIPT_URL/exec";

async function submitForm(formData) {
  try {
    await fetch(GOOGLE_SHEET_URL, {
      method: "POST",
      mode: "no-cors",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(formData)
    });
    window.location.href = "thankyou.html";
  } catch (error) {
    console.error("Submit error:", error);
    alert("Error submitting form. Please call us: (312) 909-4861");
  }
}

# In Russian + more explicit
Открой сайт sheets.google.com и создай новую пустую таблицу.

Назови этот файл <Название Компании>

	Теперь в самой первой строке (Строка 1) нужно создать те самые заголовки (хедеры). Впиши эти слова в ячейки по порядку слева направо:

Ячейка A1: Timestamp (Время)
Ячейка B1: First Name (Имя)
Ячейка C1: Last Name (Фамилия)
Ячейка D1: Phone (Телефон)
Ячейка E1: Email (Почта)
Ячейка F1: CDL Class (Категория прав)
Ячейка G1: Experience (Опыт)
Ячейка H1: State (Штат)

---

Прямо в этой таблице в верхнем меню нажми Расширения (Extensions) → Apps Script. У тебя откроется новая вкладка.

Там будет написан короткий стандартный код. Выдели его и удали полностью.

Скопируй весь код из твоей инструкции (начиная от function doPost(e) { и заканчивая }) и вставь его в пустое окно. Не переживай, если не понимаешь код — он просто говорит таблице: "когда придут новые данные, создай новую строку и вставь их по порядку".
```Это будет поподать в Лист 1
function doPost(e) {

var sheet = SpreadsheetApp.getActiveSpreadsheet().getActiveSheet();

var data = JSON.parse(e.postData.contents);


sheet.appendRow([

new Date(),

data.firstName,

data.lastName,

data.phone,

data.email,

data.cdlClass,

data.experience,

data.state

]);


return ContentService

.createTextOutput(JSON.stringify({ result: "success" }))

.setMimeType(ContentService.MimeType.JSON);}
```

``` Это будет поподать в Лист2
function doPost(e) {                                                                                                
                                                                                                                        
      var sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("Лист2");                                        
      var data = JSON.parse(e.postData.contents);                                                                       
                                                                                                                        
                                                                                                                        
      sheet.appendRow([                                                                                                 
                                                                                                                        
        new Date(),                                                                                                     
        data.firstName,                                                                                                 
        data.lastName,                                                                                                  
        data.phone,                                                                                                     
        data.email,                                                                                                     
                                                                                                                        
        data.cdlClass,                                                                                                  
        data.experience,                                                                                                
                                                                                                                        
        data.state                                                                                                      
      ]);                                                                                                               
                                                                                                                        
      return ContentService                                                                                             
        .createTextOutput(JSON.stringify({ result: "success" }))                                                        
        .setMimeType(ContentService.MimeType.JSON);                                                                     
                                                                                                                        
    } 
``` 

В правом верхнем углу нажми синюю кнопку Начать развертывание (Deploy) → Новое развертывание (New Deployment).

Нажми на значок шестеренки ⚙️ (Выберите тип) и выбери Веб-приложение (Web app).

Заполни настройки точно так:

Запуск от имени (Execute as): От моего имени / Me

У кого есть доступ (Who has access): У всех / Anyone

Нажми Начать развертывание (Deploy).

Примечание: На этом этапе Google может попросить тебя предоставить разрешения (Authorize access). Нажми "Разрешить", выбери свой аккаунт, затем нажми "Advanced" (Дополнительные настройки) и перейди по ссылке внизу "Go to Untitled project (unsafe)", чтобы разрешить скрипту работать с твоей таблицей.

Когда всё загрузится, появится окно с Web App URL (Длинная ссылка веб-приложения). Скопируй её.


Тебе нужно скопировать нижнюю ссылку — ту, которая находится под заголовком «Веб-приложение» (URL).

Она начинается с [https://script.google.com/](https://script.google.com/)...