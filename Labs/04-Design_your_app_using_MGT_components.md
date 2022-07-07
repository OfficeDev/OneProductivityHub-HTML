## Part 4 - Design your One Productivity Hub by using Microsoft Graph Toolkit components

- [Part 0 - Environment Setup](/Labs/00-Setup.md)
- [Part 1 - Create a new web app](/Labs/01-Create_new_app.md)
- [Part 2 - Register your application in Azure Active Directory](/Labs/02-Register_your_app_in_Azure_AD.md)
- [Part 3 - Integrate authentication with MSAL2 Provider](/Labs/03-Initialize_MGT_and_auth_page.md)
- [Part 4 - Design your One Productivity Hub by using Microsoft Graph Toolkit components](/Labs/04-Design_your_app_using_MGT_components.md) ( **📍 You are here** )
- [Part 5 - Test your web app](/Labs/05-Test_your_app.md)

Now, you're ready to add any of the Microsoft Graph Toolkit components to your tab.

### Design your web app with HTML and CSS

To make our app look structured, we will create three columns in a row by using some HTML and CSS code as the following:

1. Let's start with CSS. Create `index.css` file under your project and add below CCS code:

```css
body,
#root>div {
    background-color: #F3F2F1;
}


.features {
    min-height: 80vh;
    margin: 20px;
    background-color: #FFF;
    box-shadow: 0px 1.2px 3.6px rgba(0, 0, 0, 0.11), 0px 6.4px 14.4px rgba(0, 0, 0, 0.13);
    border-radius: 4px;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}


.header {
    display: flex;
    background-color: #f0f0f0;
}

.title {
   margin-top: 20px;
   margin-left: 10px;
   width: 100%;
}

.title h2 {
    
    font-size: 24px;
    padding-left: 5px;
    display: inline;
    font-weight: 600;
 
    
}

.title h3 {
    float: left;
    width: 32%;
    background:transparent;
    font-size: 16px;
    margin-bottom: 10px;
    padding-left: 10px;
    padding-top: 10px;
    color: #8A8886;
    font-weight: 600;
}


mgt-login {
   
    margin-left: 20px;
    --avatar-size: 60px;
    --font-family: 'Segoe UI';
    --font-size: 20px;
    --font-weight: 700;
    --color: black;
    --text-transform: none;
    --line2-font-size: 14px;
    --line2-font-weight: 400;
    --line2-color: #8A8886;
    --line2-text-transform: none;
}

#content, html, body {
    height: 98%;
    
  }
 
  #mgt-col {
    float: left;
    width: 32%;
    background:transparent;
    height:500px;
    overflow: hidden;
    padding: 5px;
    margin-top: 5px;
  }
  #mgt-col:hover {
    overflow-y: auto;
  }

```

1. In `index.html` under `<head></head>`, update the stylesheet link `href` as **index.css**:

```html
<link rel='stylesheet' type='text/css' media='screen' href='index.css'>
```

1. In `index.html`, add the following HTML code in `<body></body>`:

```html
<div>
  <div class="features">
  </div>
</div>
```

### Login component

In `index.html` under `<body></body>`, add the Login component inside the main div:

```html
<mgt-login></mgt-login>
```

### Add title and column for each feature in One Productivity Hub

To make our app look structured, let's create a title and a column for each feature that will be added in the One Productivity Hub moving forward. In `index.html` under `<body></body>`, add the following html code inside the div tagged with `class="features"`:

```HTML
<div class="header"><div class="title">
  <h2>One Productivity Hub</h2>
  <div class="row"><div class="column"><h3>Calendar events</h3></div>
  <div class="column"><h3>To-do tasks</h3></div>
  <div class="column"><h3>Files</h3></div>
</div></div>

<div class="row" id="content">
  <div class="column" id="mgt-col"></div>
  <div class="column" id="mgt-col"></div>
  <div class="column" id="mgt-col"></div>
</div>

```

#### Agenda component

Under div tagged with `class="row"`, add the Agenda component inside the first column div:

```HTML
<mgt-agenda></mgt-agenda>
```

#### To-do component

Under div tagged with `class="row"`, add the To-do component inside the second column div:

```HTML
 <mgt-todo></mgt-todo>
```

#### FileList component

Under div tagged with `class="row"`, add the File list component inside the third column div:

```HTML
<mgt-file-list></mgt-file-list>
```

### Final version of `index.html`

Finally, `index.html` will be as following:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset='utf-8'>
  <meta http-equiv='X-UA-Compatible' content='IE=edge'>
  <title>One Productivity Hub</title>
  <meta name='viewport' content='width=device-width, initial-scale=1'>
  <link rel='stylesheet' type='text/css' media='screen' href='index.css'>

  <script src='main.js'></script>
  <script src="https://unpkg.com/@microsoft/mgt@2.5.1/dist/bundle/mgt-loader.js"></script>
  <mgt-msal2-provider 
      client-id="2a20d081-e42e-49a1-9fef-aead08eb53dc"
      scopes="User.Read,
      User.ReadBasic.All,
      Calendars.Read,
      Files.Read,
      Files.Read.All,
      Sites.Read.All,
      Tasks.Read,
      Tasks.ReadWrite,
      People.Read,
      User.ReadBasic.All">    
  </mgt-msal2-provider>
</head>
<body>
   
  <div>
   
    <mgt-login></mgt-login>
 
    <div class="features">
      <div class="header">
        <div class="title">
          <h2>One Productivity Hub</h2>

          <div class="row">
            <div class="column">
                <h3>Calendar events</h3>
            </div>
            <div class="column">
              <h3>To-do tasks</h3>
            </div>
            <div class="column">
              <h3>Files</h3>
            </div>
          </div>
        </div>
      </div>

   
      <div class="row" id="content">

              <div class="column" id="mgt-col">
                <mgt-agenda></mgt-agenda>
              </div>
              <div class="column" id="mgt-col">
                <mgt-todo></mgt-todo>
              </div>
              <div class="column" id="mgt-col">
                <mgt-file-list></mgt-file-list>
              </div>
      </div>

    </div>
  </div>
</body>
</html>

```

## References

- Microsoft Docs - [Build a web application with the Microsoft Graph Toolkit](https://docs.microsoft.com/en-us/graph/toolkit/get-started/build-a-web-app?tabs=html%2CHTML)

## Next Step

> ▶️ **[Part 5 - Test your web app](/Labs/05-Test_your_app.md)**
