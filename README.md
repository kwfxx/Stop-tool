
import subprocess
import hashlib
import time
def run(cmd):
    try:
        out = subprocess.check_output(cmd, shell=True, stderr=subprocess.DEVNULL)
        return out.decode().strip()
    except Exception:
        return ""

android_id = run("settings get secure android_id")
serial = run("getprop ro.serialno") or run("getprop ro.boot.serialno") or run("getprop ro.hardware")
brand = run("getprop ro.product.brand")
model = run("getprop ro.product.model")
mac = run("cat /sys/class/net/wlan0/address 2>/dev/null")
values = [v for v in [android_id, serial, brand, model, mac] if v]
concat = "|".join(values)

SALT = "سِرّ_خاص_قوي_غير_مُشارَك"

full = SALT + "|" + concat
h = hashlib.sha256(full.encode()).hexdigest()
hash=['55ce387a49d064b3da5671d77a3a8895db8108b0ad347e834aa571f2fc417b40','70d1489f3944356042da509d635772dfe92ea50fe94b609c1f584e5f28a2f022','eeaed30664a309dc7b92c7a3d61b2b9fd6036dbb17984117b48543bb139c6aa5','8448df0e84a3baf0b58264bc1b538648e6e4d39ee9047645f6d687ad9d86c0d9','81941b565529ff09b45e7f9211a9114b774a4ba37c6ec5f6143e2c1fb89961e8','0f9541560ac1a2bb629ee473c175a222818f306524f4ef8b4e4b2751a46eb021','9cf078cb0adcf967163357c07fe785223b17ab1c8783eebaa6ba1c62a61f510c','66d3953702e69fec3eb9e1f30b654ec3f9291f38c1153d2eac8087e4a6631520']
if h in hash:
    print('good / هاتفك مصرح للدخول ')
    pass
else :
	while True:
	   print('your code is /', h)
	   print()
	   print('الاداة مدفوعه راسل المطور يفعل لك @FFNZZ')
	   time.sleep(90)
     
