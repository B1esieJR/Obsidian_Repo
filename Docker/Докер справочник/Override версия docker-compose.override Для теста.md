
services:  
  backend:  
    build:  
      dockerfile: Dockerfile.dev  
    environment:  
      - NODE_ENV=development  
    volumes:  
      - ./backend/src:/app/src  
      - ./backend/docs:/app/docs
        
        