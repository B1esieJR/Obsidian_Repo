
services:  
  backend:  
    build:  
      dockerfile: Dockerfile  
    environment:  
      - NODE_ENV=production  
    ports:  
      - "${BACKEND_PORT}:3000"  
      - "${WEBSOCKET_PORT}:3015"  
    volumes:  
      - ./backend/docs:/app/docs