# caido-parser 1 liner 
```sh
jq '.[] | select(.host? and (.host | test("(^|\\.)vercel\\.app$")) and (.response? and .response.status_code == 200)) | .host + .path' 'filename.json'
```
- change the domain to desired
- status code of desired
