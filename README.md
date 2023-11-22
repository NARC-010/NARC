https://docs.google.com/document/d/1JkGlyT47t9DJf2oMne6-1-6b8Tp-RbbM/edit?usp=sharing&ouid=102539893821167373027&rtpof=true&sd=true

##############################################

#index.html

##############################################

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Screen Share</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/socket.io/3.1.3/socket.io.js"></script>
    <script>
        var socket = io.connect('http://' + document.domain + ':' + location.port);

        document.addEventListener('keydown', function (event) {
            socket.emit('key_down', { key: event.key });
        });

        document.addEventListener('keyup', function (event) {
            socket.emit('key_up', { key: event.key });
        });

        document.addEventListener('click', function () {
            socket.emit('mouse_click');
        });
    </script>
</head>
<body>
    <img id="screen" src="" alt="Screen Share">
    <script>
        socket.on('update_screen', function (data) {
            document.getElementById('screen').src = 'data:image/jpeg;base64,' + data;
        });
    </script>
</body>
</html>

##############################################

#app.py

##############################################

from flask import Flask, render_template
from flask_socketio import SocketIO
import pyautogui

app = Flask(__name__)
socketio = SocketIO(app)

@app.route('/')
def index():
    return render_template('index.html')

@socketio.on('key_down')
def handle_key_down(data):
    key = data['key']
    pyautogui.keyDown(key)

@socketio.on('key_up')
def handle_key_up(data):
    key = data['key']
    pyautogui.keyUp(key)

@socketio.on('mouse_click')
def handle_mouse_click():
    pyautogui.click()

if __name__ == '__main__':
    socketio.run(app, debug=True, use_reloader=False, host='0.0.0.0', port=5000)
    
