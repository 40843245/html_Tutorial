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
  
## Ref
