+++
title = "Contact"
author = "Houston Haynes"
cssFiles = "/js/contact.js"
+++ 
{{< rawhtml >}}
<div id="container" class="ld-over">
  <div id="output"></div> 
      <form id="submitMessage" method="post" style="visibility:visible;"> 
        <div class="form-group"> 
          <input type="text" id="name" class="form-control" placeholder="Your name" required>
        </div>
        <div class="form-group">
          <input type="email" id="email" class="form-control" placeholder="Your email" required>
        </div>
        <div class="form-group">
          <textarea id="message" class="form-control" placeholder="Type your message..." required></textarea>
        </div>
        <input class="button-primary" type="submit" value="Submit">
      </form>
</div>
<div class="lds-heart centered">
  <div><img id="AzureFunctionHeartbeat" src="/img/Function Apps.svg" height="50" width="50" style="vertical-align:middle;visibility:hidden;"/></div>
</div>
{{< /rawhtml >}}