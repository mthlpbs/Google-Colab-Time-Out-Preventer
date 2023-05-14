# Google-Colab-Time-Out-Preventer
Google timeout preventer is a code snippet that prevents Google Colab from timeout. Timeout is when Google Colab disconnects the session due to inactivity or network issues. The code snippet uses IPython and google.colab modules to click the connect button every 60 seconds automatically, which keeps the session alive and prevents timeout.
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
