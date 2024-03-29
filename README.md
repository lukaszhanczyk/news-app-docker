# News App Project

Application for viewing articles downloaded from APIs:
</br>https://newsapi.org/
</br>https://open-platform.theguardian.com/
</br>https://developer.nytimes.com/

Users can create accounts and save their own filters for viewing saved articles

## Technology

- PHP 8.2
- Node 18.15.0
- Mysql 5.7

## Instalation

1. Create folder `news-app` on your computer and clone the repositories given below into it
   </br>[news-app-react](https://github.com/lukaszhanczyk/news-app-react)
   </br>[news-app-laravel](https://github.com/lukaszhanczyk/news-app-laravel)
   </br>[news-app-docker](https://github.com/lukaszhanczyk/news-app-docker)</br>
   </br>
2. The directory tree should look like this

   ```bash
   ── news-app
      ├── news-app-react
      ├── news-app-laravel
      └── news-app-docker
   ```
3. In each of the above-mentioned projects, copy `.env.example` and save it under the name `.env` in your project folders


4. Open `news-app-docker` directory and in terminal use command

   ```bash
   docker-compose up --build
   ```

5. After the containers start correctly, open in the same folder (`news-app-docker`) new terminal and enter backend container bash

   ```bash
   docker exec -it --user www-data backend bash
   ```


** In point 4 and 5 you may need administrator privileges (in Linux, use commands with the `sudo` prefix)

   ```bash
    sudo docker-compose up --build
    sudo docker exec -it --user www-data backend bash
   ```
** If backend container have different name, please change `backend` to this name in command from point 5

6. In bash generate key, push migrations, seed and downland articles using custom command  

   ```bash
   php artisan key:generate
   php artisan migrate
   php artisan db:seed
   php artisan app:update-news-command
   ```
The application is running on port 3000

[ http://localhost:3000/]( http://localhost:3000/)

