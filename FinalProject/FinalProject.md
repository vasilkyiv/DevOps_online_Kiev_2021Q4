https://www.youtube.com/watch?v=xRuG2WDACK8&list=PLg5SS_4L6LYujWDTYb-Zbofdl44Jxb2l8&index=21

https://www.youtube.com/watch?v=3c-iBn73dDE

https://www.simplilearn.com/tutorials/docker-tutorial/getting-started-with-docker?source=sl_frs_nav_playlist_video_clicked

****************************************************
    1) docker network create mongo-network


    2)  docker run  -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongodb --net mongo-network\
    mongo
    
    docker run  -d \ 
    -p 27017:27017 \
    -e MONGO_INITDB_ROOT_USERNAME=admin \
    -e MONGO_INITDB_ROOT_PASSWORD=password \
    --name mongodb \
    --net mongo-network\
    mongo

output:
ce70c7f8321b076f3ff82c2f178e685d9c2d38e5df1b5d25d433aeb9f92bf71d

    3) docker run  -d \ 
    -p 8081:8081 \
    -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
    -e  ME_CONFIG_MONGODB_ADMINPASSWORD=password \
    --net mongo-network\
    --name mongo-express  \
    -e ME_CONFIG_MONGODB_SERVER 