# Button events
Button events can be set in the attribute of the tag <button>.

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
 
In the above example, once I clicked the "Play" Button, the onclick event is triggered.
  
Executing the code.
  
 onclick="onClicked()"
  
Additionally, it is equivalent to assign all contents of the function as a string to onclick event.
  
(But I don't recommend, since it looks so ugly, NOT easily read and troublesome to escape the double-quote symbols).
  
 i.e. They are equivalent.
  
  
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
 
  and
  
  <!DOCTYPE html>

      <html>
  
      <body>
    
        <button onclick="let h1id=document.getElementById(\"h1id\"); h1id.innerText=\"Clicked.\";">Play</button>
    
        <h1 id="h1id">This is h1</h1>
    
        <script>
      
          function onClicked()
      
          {
          
      
          }
      
        </script>
    
      </body>
  
      </html>
 
  
## Ref
