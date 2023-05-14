# Google-Colab-Time-Out-Preventer
```
#@title <b>Time Out Preventer (Advanced) </b></strong>
%%capture
AUTO_RECONNECT = True #@param {type:"boolean"}
#@markdown **Run this code to prevent Google Colab from Timeout**
from os import makedirs
makedirs("/root/.config/rclone", exist_ok = True)
if AUTO_RECONNECT:
  import IPython
  from google.colab import output

  display(IPython.display.Javascript('''
  function ClickConnect(){
    btn = document.querySelector("colab-connect-button")
    if (btn != null){
      console.log("Click colab-connect-button"); 
      btn.click() 
      }
    
    btn = document.getElementById('ok')
    if (btn != null){
      console.log("Click reconnect"); 
      btn.click() 
      }
    }
    
  setInterval(ClickConnect,60000)
  '''))
  ```
