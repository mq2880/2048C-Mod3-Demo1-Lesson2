# 2048C-Mod3-Demo1-Lesson2

### Demonstration: Manipulating the DOM with Javascript

#### Preparation Steps 

Ensure that you have cloned the 20480C directory from GitHub (**https://github.com/MicrosoftLearning/20480-Programming-in-HTML5-with-JavaScript-and-CSS3/tree/master/Allfiles**). It contains the code segments for the labs and demos in this course. 

#### Demonstration Steps

#### Create new project

1. Open **Microsoft Visual Studio**.
2. In **Microsoft Visual Studio**, on the **File** menu, point to **New**, and then click **Project**.
3. In the **New Project** dialog box, in the left pane, under **Installed**, expand the **Visual C#** node, and then click the **Web** node.
4. Click **ASP.NET Web Application(.NET Framework)**.
5. In the **Name** box, enter **HtmlDOMSample**.
6. In the **Location** box, enter **[Repository root]Allfiles\Mod03\Labfiles\Starter\Exercise 2**, and then click **OK**.
7. In **New ASP.NET Web Application- HtmlDOMSample** dialog box, Select **MVC** and then click **OK**.

#### Add the index page

1.	In **HtmlDOMSample - Microsoft Visual Studio**, on the **Project** menu, click **Add New Item**.
2.	In the **Add New Item – HtmlDOMSample** dialog box, click **HTML Page**.
3.	In the **Name** box, enter **index.html**.
4.	Click **Add**.
5.	Open the **index.html** file.
6.	In the file, add the following code:

 <!DOCTYPE html>
     <html>
     <head>
         <meta charset="utf-8" />
         <meta name="viewport" content="width=device-width, initial-scale=1.0">
         <title>HTML Basic</title>
         <link href="/Content/Site.css" rel="stylesheet" type="text/css" />
         <link href="/Content/bootstrap.min.css" rel="stylesheet" type="text/css" />
         <script src="/Scripts/modernizr-2.6.2.js"></script>
     </head>
     <body>
         <div class="navbar navbar-inverse navbar-fixed-top">
             <div class="container">
                 <div class="navbar-header">
                     <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
                         <span class="icon-bar"></span>
                         <span class="icon-bar"></span>
                         <span class="icon-bar"></span>
                     </button>

                 </div>
                 <div class="navbar-collapse collapse">
                     <ul class="nav navbar-nav"></ul>
                 </div>
             </div>
         </div>
    
         <div class="container body-content">
             <form>
                 <fieldset>
                     <legend>
                         Enter your details
                     </legend>
                     <ol>
                         <li>
                             <label>
                                 <strong>Full name</strong>
                                 <br />
                                 <input type="text" name="UserName" />
                             </label>
                         </li>
                         <li>
                             <label>
                                 Telephone number
                                 <br />
                                 <input type="text" name="Phone" />
                             </label>
                         </li>
                         <li>
                             <label>
                                 Email Address
                                 <br />
                                 <input type="text" name="Email" />
                             </label>
                         </li>
                         <li>
                             <label>
                                 My hobbies
                             </label>
                             <div id="hobbiesList">
                                 <input type="text" name="hobby" class="hobbiesInput" />
                                 <button type="button" id="newHobbyBtn">Add hobby</button>
                             </div>
                         </li>
                     </ol>
                 </fieldset>
                 <input type="submit" value="Check my details" />
             </form>
         </div>
     </body>
     </html>
#### Add the JavaScript file

1. Right-click the **Scripts** folder, select **Add**, and then click **New Item**.

2. In the **Add New Item – HtmlDOMSample** dialog box, click **JavaScript File**.

3. In the **Name** box, enter **indexScript.js**.

4. Click **Add**.

5. Open the **indexScript.js** file.

6. To create a **createNode** function that receives the html element name and returns the html element, enter the following code:

   ```javascript
        function createNode(element) {
            return document.createElement(element);
        }
   ```

7. To create an **append** function that receives the parent and child elements and appends the child to the parent, enter the following code:

   ```javascript
        function append(parent, el) {
            return parent.appendChild(el);
        }
   ```

8. Create an **addHobbies** function by adding the following code:

```javascript
        function addHobbies () { }
```

9. To get all the inputs with the **hobbiesInput** class into the *const* variable, enter the following code:

   ```javascript
       const inputList = document.querySelectorAll('.hobbiesInput');
   ```

10. To check that **inputList** contains less than five elements, add new inputs with the **createNode** and **append** functions,  and if **inputList** contains more than five elements, remove the event listener, and then enter the following code:

    ```javascript
        if (inputList.length < 5) {
        
            const hobbiesList = document.getElementById('hobbiesList');        
            const newLineElement = createNode('br'),
            inputElement = createNode('input');
        
            inputElement.setAttribute("class", "hobbiesInput");
        
            append(hobbiesList, newLineElement);
            append(hobbiesList, inputElement);
        }
        else {
            document.getElementById('newHobbyBtn').removeEventListener('click', addHobbies);
        }
    ```

11. On the JavaScript page, to add an event listener on **DOMContentLoaded**, enter the following code:

    ```javascript
        document.addEventListener('DOMContentLoaded', function (event) {
            
        });
    ```

12. To get a **newHobbyBtn** button by **getElementById**, add an event listener on the button, and attach an **addHobbies** function, enter the following code:

    ```javascript
        document.getElementById('newHobbyBtn').addEventListener('click', addHobbies);
    ```

13. On the **index.html** page, to the **&lt;Head&gt;** element, add the folowing script tag:

    ```html
        <script src="/Scripts/indexScript.js"></script>
    ```

#### Run the web application

1.	In Solution Explorer, double-click **Properties**.
2.	In the left pane, click **web**.
3.	Select **Specific Page**, click **...**, and then select **Index.html** and click **OK**. 
4.	Click **IIS Express (Microsoft Edge)**.
5.	In the **HTML Basic** window, on the input box below the label **My hobbies**, type a hobby and then click the **Add hobby** button. Repeat this step 5 times.
6.	Verify you cannot add more than 5 hobbies.
7.	In **HtmlDOMSample - Microsoft Visual Studio**, on the **Debug** menu click **Stop Debugging**.
8.	Close all open windows.