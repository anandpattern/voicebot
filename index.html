const express = require('express');
const http = require('http');
const { WebSocketServer, WebSocket } = require('ws');
const path = require('path');

const API_KEY = process.env.SUN_API_KEY || 'YOUR_API_KEY_HERE';
const SUN_WS = 'wss://api.getsun.io/ws';
const PORT = 3000;

const app = express();
app.use(express.static(path.join(__dirname)));

const server = http.createServer(app);
const wss = new WebSocketServer({ server, path: '/ws' });

wss.on('connection', (clientWs) => {
  console.log('Browser connected, opening Sun WebSocket...');

  const sunWs = new WebSocket(SUN_WS, {
    headers: { 'Authorization': `Bearer ${API_KEY}` }
  });

  sunWs.on('open', () => {
    console.log('Connected to Sun API');
  });

  sunWs.on('message', (data) => {
    if (clientWs.readyState === WebSocket.OPEN) {
      clientWs.send(data.toString());
    }
  });

  sunWs.on('close', (code, reason) => {
    console.log(`Sun closed: ${code} ${reason}`);
    if (clientWs.readyState === WebSocket.OPEN) {
      clientWs.close(code, reason.toString());
    }
  });

  sunWs.on('error', (err) => {
    console.error('Sun error:', err.message);
    clientWs.close();
  });

  clientWs.on('message', (data) => {
    if (sunWs.readyState === WebSocket.OPEN) {
      sunWs.send(data.toString());
    }
  });

  clientWs.on('close', () => {
    console.log('Browser disconnected');
    if (sunWs.readyState === WebSocket.OPEN) {
      sunWs.close();
    }
  });
});

server.listen(PORT, () => {
  console.log(`Server running at http://localhost:${PORT}`);
});
