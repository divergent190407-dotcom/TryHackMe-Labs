## basics
- On Firefox, press Ctrl + Shift + K
- On Google Chrome, press Ctrl + Shift + J
- On Safari, press Command + Option + J
- Alert: You can use the alert() function to display a JavaScript alert in a web browser. Try alert(1) or alert('XSS') (or alert("XSS")) to display an alert box with the number 1 or the text XSS.
- Console log: Similarly, you can display a value in the browser’s JavaScript console using console.log(). Try the following two examples in the console log: console.log(1) and console.log("test text") to display a number or a text string.
- Encoding: The JavaScript function btoa("string") encodes a string of binary data to create a base64-encoded ASCII string. This is useful to remove white space and special characters or encode other alphabets. The reverse function is atob("base64_string").
## types of xss 
- Reflected XSS: This attack relies on the user-controlled input reflected to the user. For instance, if you search for a particular term and the resulting page displays the term you searched for (reflected), the attacker would try to embed a malicious script within the search term.
- a search query containing <script>alert(document.cookie)</script>
- Stored XSS: This attack relies on the user input stored in the website’s database. For example, if users can write product reviews that are saved in a database (stored) and being displayed to other users, the attacker would try to insert a malicious script in their review so that it gets executed in the browsers of other users.
- DOM-based XSS: This attack exploits vulnerabilities within the Document Object Model (DOM) to manipulate existing page elements without needing to be reflected or stored on the server. This vulnerability is  the least common among the three.
 
