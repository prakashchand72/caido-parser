# caido-parser 1 liner 
```sh
jq '.[] | select(.host? and (.host | test("(^|\\.)vercel\\.app$")) and (.response? and .response.status_code == 200)) | .host + .path' 'filename.json'
```
- change the domain to desired
- change status code to desired
# usage
![image](https://github.com/user-attachments/assets/79e74fb9-ffa8-4c23-9bd2-dccd23c69654)
