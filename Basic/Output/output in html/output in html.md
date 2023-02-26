# Output results in a webbrowser in html 
Step 1:

Get the object.

Step 2:

Set the attribute innerText of the object.

## Example
Ex1:

    <!DOCTYPE html>

    <html>
  
      <body>
    
        <button onclick="onClicked()">Play</button>
    
        <h1 id="h1id">This is h1</h1>
    
        <script>
      
          function onClicked()
      
          {
          let h1id=document.getElementById("h1id");
      
          h1id.innerText="Clicked.";
      
          }
      
        </script>
    
      </body>
  
    </html>

In the above example, when I click the "Play" Button, it will invoke onClicked()

Then the object with element whose id is "h1id" will be fetched.

By reassigning the attribute of h1id, we can set the text.


## Ref

https://www.w3schools.com/js/js_htmldom_document.asp
