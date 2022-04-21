# axios
### json-server的使用（模拟数据）
    npm 安装后，直接运行json-server --watch db.json
### axios的默认配置
        axios.defaults.method = 'GET';//设置默认的请求类型为 GET
        axios.defaults.baseURL = 'http://localhost:3000';//设置基础 URL
### axios创建实例
     const duanzi = axios.create({
                baseURL: 'https://api.apiopen.top',
                timeout: 2000
            });
### axios的请求拦截器和相应拦截器
##### 请求拦截器
    axios.interceptors.request.user((config)=>{
        //修改 config 中的参数
          config.params = {a:100};
          return config;
    },(error)=>{
          return Promise.reject(error);
    })
    
##### 响应拦截器
            axios.interceptors.response.use(function (response) {
                console.log('响应拦截器 成功 1号');
                return response.data;
                // return response;
            }, function (error) {
                console.log('响应拦截器 失败 1号')
                return Promise.reject(error);
            });
### axios的取消请求
     cancelToken: new axios.CancelToken((c) => {
          //3. 将 函数c 的值赋值给 cancel  然后在外调用cancel就行。
               cancel = c;
            })
