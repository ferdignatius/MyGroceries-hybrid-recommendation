# MyGroceries
Recommendation System Implementation on a groceries management system between end-consumer and supermarkets

Because the dataset is too large (> 100MB), you need to insert the dataset folder seperately.
Download the dataset here : https://www.kaggle.com/datasets/yasserh/instacart-online-grocery-basket-analysis-dataset
Make sure the dataset format are as follow:  
+-------------------------------------------+  
instacart  
L aisles.csv  
L departments.csv  
L order_products__prior.csv  
L order_products__train.csv  
L orders.csv  
L products.csv  
+-------------------------------------------+  
Put the dataset folder inside folder ai/...(insert here) and folder backend/uploads/...(insert here too)


# How to run the application
Video Tutorial Setup : https://youtu.be/3JkohB_mfHQ  

1) Import Project dari Github 
GitHub Link : https://github.com/Antiveg/MyGroceries  
Project bisa di-clone dengan command git atau menggunakan GUI Github Desktop. Project 
kami tidak bisa diletakkan langsung ke dalam zip folder karena file size project yang melebihi 
10 MB yang merupakan batas maksimum pengumpulan zip folder dalam BINUS Maya. 

2) Setup & Run Frontend Server 
• Buka folder project dalam VS Code 
• cd ./frontend untuk redireksi ke frontend folder dari project root folder 
• Install library npm yang dibutuhkan dengan cmd npm install, pastikan sudah download 
node.js pada laptop/PC. 
• Copy dan Paste file .env-example, lalu rename menjadi .env 
• Dalam .env, isilah kredensial variabel env seperti berikut - 
VITE_BACKEND_BASEURL='http://localhost:5000' - - 
VITE_UPLOADS_BASEURL='http://localhost:5000/uploads' 
VITE_PROJECT_STATUS="development" 
• Run server dengan cmd npm run dev 

3) Setup & Run Backend Server 
• Buka folder project dalam VS Code 
• cd ./backend untuk redireksi ke backend folder dari project root folder 
• Install library npm yang dibutuhkan dengan cmd npm install, pastikan sudah download 
node.js pada laptop/PC. 
• Pastikan sudah download postgresql DB melalui https://www.postgresql.org/download/ 
• Buka GUI pgAdmin lalu buatlah database baru bernama (bebas), disini TEMP 
• Copy dan Paste file .env-example, lalu rename menjadi .env 
• Dalam .env, isilah kredensial variabel env seperti berikut - 
NODE_ENV=development - - - - - - - - - 
DB_HOST_DEV=127.0.0.1 
DB_USER_DEV=[username user dalam database postgresql] 
DB_PASS_DEV=[password database postgresql user] 
DB_NAME_DEV=[nama database yang baru dibuat] 
DB_DIALECT_DEV=postgres 
JWT_SECRETKEY=[kata bebas (tidak boleh spasi/angka)] 
PORT=5000 
AI_SERVER_DEV=http://127.0.0.1:8000 
FRONTEND_SERVER_DEV=http://localhost:5173 
• Membuat entitas database dengan cmd npx sequelize-cli db:migrate 
• Mengisi database dengan data melalui cmd npx sequelize-cli db:seed:all 
• Run server dengan cmd nodemon server.js 

4) Setup & Run AI Server 
• Buka folder project dalam VS Code 
• cd ./ai untuk redireksi ke ai folder dari project root folder 
• Pastikan sudah download miniconda melalui https://www.anaconda.com/docs/getting
started/miniconda/install  
• Buka miniconda command prompt, execute cmd conda create -n [nama env bebas] 
• Lanjut execute cmd conda activate [nama env yang baru dibuat] 
• Lanjut execute cmd conda install -c conda-forge pip=24.2 scikit-surprise=1.1.4 numpy 
fastapi uvicorn scikit-learn pandas scipy nltk 
• Kembali ke VS Code, Pilih untuk menggunakan kernel / env python miniconda yang baru 
dibuat sebelumnya. Dalam VS Code bisa dengan shortcut CTRL + Shift + P atau View → 
Command Palette, lalu pilih nama env yang baru dibuat 
• Run ai server dengan cmd uvicorn main:app --reload

