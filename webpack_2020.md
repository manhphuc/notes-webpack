### 1. Cài đặt webpack bằng npm
__Bước 1:__ Trong thư mục gốc của theme, khởi tạo npm bằng câu lệnh sau trong Terminal:  
`$ npm init -f`  
- Thêm __-f__ trong câu lệnh trên để tạo nhanh file, bỏ qua các bước hướng dẫn. Lúc này, chúng ta sẽ thấy file package.json đã được tạo trong folder theme. 

__Bước 2:__ Sau khi tạo được package.json, chúng ta sẽ tiến hành cài đặt package webpack và webpack cli bằng các câu lệnh sau:  
 
 Để cài đặt bản phát hành mới nhất hoặc một phiên bản cụ thể, hãy chạy một trong các lệnh sau:  
```sh
$ npm install --save-dev webpack
# Hoặc phiên bản cụ thể
$ npm install --save-dev webpack@<version>
```

__Bước 3:__ Vì webpack chỉ hỗ trợ chuyển đổi giữa các file js nên chúng ta cần phải cài đặt các loader để thực thi các file css và scss. Tiến hành cài đặt các dependencies và các loaders sau:  
`$ npm install style-loader css-loader sass-loader node-sass  --save`  

- __style-loader:__ Để load các phần tử trong thẻ `<style>`  
- __css-loader:__ Để xử lý file css  
- __scss-loader:__ Để xử lý và đóng gói các file sass/scss thành file css  
- __node-scss:__ Để xử lý các file scss-loader chúng ta cần phải cài đặt thêm Node Sass hoặc Dart Sass.  

`$ npm i --save-dev mini-css-extract-plugin optimize-css-assets-webpack-plugin`  
- __mini-css-extract-plugin:__ Plugin này sẽ chia css thành các file nhỏ, sau đó tạo 1 file js chứa các css đó.  
- __optimize-css-assets-webpack-plugin:__ Plugin này sẽ tiến hành tìm kiếm các css assets khi webpack tối ưu hoá css.  

__Bước 4:__ Cài đặt Loader cho file JS  
Nếu chúng ta sử dụng JS từ các phiên bản ES6 trở lên, cần cài đặt Babel trong webpack để chuyển đổi về JS thuần. 

Trong Terminal sử dụng câu lệnh sau để cài đặt:

`$ npm install @babel/core --savesecond:npm i --save-dev babel-loader babel-preset-env uglifyjs-webpack-plugin`  
- __uglifyjs-webpack-plugin:__ Dùng để tối ưu dung lượng code.
### 2. Thay đổi nội dung package.json và webpack.config.js
__Bước 1:__ Tạo file app.js trong thư mục ThemeName/assets/src/app/javascripts. Trong file này, chúng ta sẽ bao gồm các stylesheet file được yêu cầu để webpack thực thi:  
```sh
// js/app.js

// Require scripts
require('./main.js');

// Require scss
require('../scss/main.scss'); 
```
__Bước 2:__ Vào file package.json để thay đổi các thông tin phù hợp với project như sau:  
- Tệp đính kèm trong source

Đối với các package đã được cài đặt bằng npm:  
__devDependencies__ là những module sẽ chỉ được dùng vào mục đích phát triển sản phẩm trong khi dependencies là những module sẽ được sử dụng trong quá trình chạy sản phẩm thực tế.  
Để lưu một package từ __dependencies__ sang __devDependencies__, thêm `–save-dev` sau một sau câu lệnh trong quá trình cài đặt package. Giả sử mình muốn cài đặt một package bootstrap và khai báo chúng trong mục __devDependencies__ thì câu lệnh của mình sẽ như sau: `$ npm install bootstrap –save-dev`.

__Bước 3:__ Điều chỉnh file `webpack.config.js` trong thư mục gốc của theme.  
- Tệp đính kèm trong source

### 3. Cài đặt packages hỗ trợ  
#### 1. Cài đặt Webpack auto-compile
#### 2. Cài đặt Error Notification
Với webpack, postcss-loader sẽ giúp chung ta tự động thêm các tiền tố đó:  

`$ npm i -D postcss-loader`  

#### 3. Cài đặt Autoprefixer
  
----------
__Chạy npm để webpack thực thi và đóng gói các file bằng câu lệnh sau trong Terminal:__  
`$ npm run build`

