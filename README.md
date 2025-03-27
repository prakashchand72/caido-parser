# caido-parser 1 liner 
```sh
jq -r '.[] | select(.host? and (.host | test("(^|\\.)vercel\\.app$")) and (.response? and .response.status_code == 200)) | .host + .path' 'filename.json'
```
- change the domain to desired
- change status code to desired
# usage
![image](https://github.com/user-attachments/assets/1fbbe55f-b671-408b-9ece-adc975ecddd2)

# Additional 
- if you want multiple status code response may be 403 or 200
```sh
jq -r '.[] | select(.host? and (.host | test("(^|\\.)vercel\\.app$")) and (.response? and (.response.status_code == 200 or .response.status_code == 403))) | .host + .path' 'filename.json'
```
- you can also chain with httpx for probling
- you can also chain up with nuclei
```
jq -r '.[] | select(.host? and (.host | test("(^|\\.)vercel\\.app$")) and (.response? and (.response.status_code == 200 or .response.status_code == 403))) | .host + .path' 'filename.json' | nuclei --silent -t ~/templete | tee -a nuclei.log
```
# Feeding proxy
```
while IFS= read -r url; do curl -x 127.0.0.1:8080 "$url"; done < urls.txt
```
