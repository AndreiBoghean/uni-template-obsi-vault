/*
```javascript
*/

ea.reset()

const files = app.vault.getFiles()
const filePaths = files.map((f)=>f.path);
// let filePaths_is = Array.from(Array(filePaths.length).keys()
filename = await utils.suggester(filePaths, filePaths,"Select a file");

if(!filename) return;

const file_count = parseInt(await utils.inputPrompt("number of last file?",null,"NaN"));
if(file_count === "NaN") return;


let str_start = filename.slice(0, filename.lastIndexOf("-")+1)
let str_mid = filename.slice(filename.lastIndexOf("-")+1, filename.lastIndexOf("."))
let str_end = filename.slice(filename.lastIndexOf("."))

for (let i = parseInt(str_mid) ; i <= file_count ; i++ )
{
	let newPath = str_start + i.toString() + str_end
	if (file_count > 10) { newPath = str_start + i.toString().padStart(2, "0") + str_end }
	let newFile = files.find(fil => fil.path === newPath);
	
	(async () => {
		await ea.addImage(0, 0, newFile);//, !event.altKey);
		ea.addElementsToView(true, false, true);
		ea.reset()
	})();
}
