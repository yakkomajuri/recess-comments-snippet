# Recess Comments Widget (Alpha)

A "serverless" comments widget for personal websites and blogs using [Recess](https://github.com/yakkomajuri/recess).

![recess widget screenshot](recess-widget.png)

## use on your website

Include the following inside your `<head>` tags:

```html
<script>
!function(){var e="";var t="\n        .recess-comment-container {\n            display: flex !important;\n            gap: 16px !important;\n            padding: 8px !important;\n            border-bottom: 1px solid #eaeaea !important;\n            background: white !important;\n            border-radius: 8px !important;\n            margin-bottom: 12px !important;\n\n        }\n\n        .recess-comment-avatar img {\n            width: 50px !important;\n            height: 50px !important;\n            border-radius: 25px !important;\n        }\n\n        .recess-comment-body {\n            display: flex !important;\n            flex-direction: column !important;\n            width: 100% !important;\n        }\n\n        .recess-comment-header {\n            display: flex !important;\n            justify-content: space-between !important;\n            margin-bottom: 8px !important;\n        }\n\n        .recess-comment-author, .recess-comment-date {\n            cursor: pointer !important;\n        }\n\n        .recess-comment-date {\n            color: #999 !important;\n            font-size: 12px !important;\n        }\n\n        .recess-comment-content {\n            font-size: 14px !important;\n        }\n\n        .recess-main-text {\n            font-size: 16px !important;\n            margin: auto !important;\n            text-align: center !important;\n            margin-bottom: 8px !important;\n        }\n\n        .recess-comment-input-container {\n            margin-top: 20px !important;\n            background-color: #ffffff !important;\n            padding: 16px !important;\n            border-radius: 8px !important;\n            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1) !important;\n            border: 1px solid #eaeaea !important;\n            display: flex !important;\n            flex-direction: column !important;\n            gap: 10px !important;\n            margin-bottom: 12px !important;\n        }\n\n        .recess-comment-textarea {\n            width: 100% !important;\n            padding: 8px !important;\n            border-radius: 8px !important;\n            border: 1px solid #eaeaea !important;\n            resize: vertical !important;\n            box-sizing: border-box !important;\n            background-color: #efefef !important;\n            font-family: inherit !important;\n        }\n\n        .recess-comment-textarea:focus {\n            border: 1px solid gray !important;\n        }\n\n        .submit-recess-comment-button {\n            align-self: flex-end !important;\n            padding: 8px 16px !important;\n            border-radius: 8px !important;\n            border: none !important;\n            color: white !important;\n            background-color: #1890ff !important;\n            cursor: pointer !important;\n        }\n\n        .submit-recess-comment-button:disabled {\n            background-color: #a0a0a0 !important;\n            cursor: not-allowed !important;\n        }\n    ",n=document.createElement("style");function o(e){const t=document.getElementById("recess");if(!t)return void console.error('"recess" div not found. Please ensure your page includes a div with id="recess".');e.forEach((e=>{const n=document.createElement("div");n.className="recess-comment-container";const o=document.createElement("div");o.className="recess-comment-avatar",o.style.cursor="pointer";const a=document.createElement("img");a.src=`https://www.gravatar.com/avatar/${e.comment_user_email_hash}?s=64&d=mp`,a.alt=e.comment_username,o.appendChild(a);const r=document.createElement("div");r.className="recess-comment-body";const m=document.createElement("div");m.className="recess-comment-header";const s=document.createElement("span");s.className="recess-comment-author",s.style.cursor="pointer",s.textContent=e.comment_username;const c=document.createElement("span");c.className="recess-comment-date",c.textContent=function(e){const t=new Date,n=new Date(e),o=Math.round((t.getTime()-n.getTime())/1e3),a=Math.round(o/60),r=Math.round(a/60),m=Math.round(r/24);return a<60?`${a} minutes ago`:r<24?`${r} hours ago`:1===m?"yesterday":m<7?`${m} days ago`:`${n.getDate().toString().padStart(2,"0")}/${(n.getMonth()+1).toString().padStart(2,"0")}/${n.getFullYear()}`}(new Date(e.comment_timestamp)),m.appendChild(s),m.appendChild(c);const i=document.createElement("div");i.className="recess-comment-content",i.textContent=e.comment_content,r.appendChild(m),r.appendChild(i),n.appendChild(o),n.appendChild(r),t.appendChild(n)}));const n=document.createElement("div"),o=document.createElement("p");o.className="recess-main-text",o.innerHTML='Comments powered by <a href="https://app.recessfeed.com" target="_blank">Recess</a>.',n.appendChild(o),t.appendChild(n)}n.styleSheet?n.styleSheet.cssText=t:n.appendChild(document.createTextNode(t)),document.getElementsByTagName("head")[0].appendChild(n),fetch(`https://us.recessfeed.com/api/posts?post_url=${encodeURIComponent(`${window.location.origin}${window.location.pathname}`)}`).then((e=>e.json())).then((t=>{t.length>0&&(e=t[0].post_uuid,function(){const t=document.getElementById("recess");if(t){t.innerHTML="";var n=document.createElement("div");n.innerHTML='\n            <div class="recess-comment-input-container">\n                <textarea rows="4" class="recess-comment-textarea" id="post-recess-comment-textarea" placeholder="Write a comment..." maxLength="1000"></textarea>\n                <button onclick="handleSubmitComment()" class="submit-recess-comment-button">Add Comment</button>\n            </div>\n        ',window.handleSubmitComment=function(){const t=document.getElementById("post-recess-comment-textarea").value;window.location=`https://app.recessfeed.com/post/${e}?comment_text=${encodeURIComponent(t)}`},t.appendChild(n)}else console.error('"recess" div not found. Please ensure your page includes a div with id="recess".')}(),fetch(`https://us.recessfeed.com/api/post_comments?post_url=${encodeURIComponent(`${window.location.origin}${window.location.pathname}`)}`).then((e=>e.json())).then((t=>{t.length>0&&(e=t[0].post,o(t))})).catch((e=>console.error("Error fetching comments:",e))))})).catch((e=>console.error("Error fetching comments:",e)))}();
</script>
```

Then on your HTML, where you want the comments to appear, add:

```html
<div id='recess'></div>
```
