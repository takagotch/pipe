### pipe
---
https://github.com/b3log/pipe

```go
var logger *log.Logger

func init() {
  rand.Seed(time.Now().UTC().UnixNano())
  
  log.SetLevel("warn")
  logger = log.NewLogger(os.Stdout)
  
  model.LoadConf()
  util.LoadMarkdown()
  i18n.Load()
  theme.Load()
  replaceServerConf()
  
  if "dev" == model.Conf.RuntimeMode {
    gin.SetMode(gin.DebugMode)
  } else {
    gin.SetMode(gin.ReleaseMode)
  }
  gin.DefaultWriter = io.MultiWriter(os.Stdout)
}

func main() {
  service.ConnectDB()
  service.Upgrade.Perform()
  cron.Start()
  
  router := controller.MapRoutes()
  server := &http.Server{
    Addr: "0.0.0.0:" + model.Conf.Port,
    Handler: router,
  }
  
  handleSignal(server)
  
  logger.Info("Pipe (v%s) is running [%s]", model.Version, model.Conf.Server)
  server.ListenAndServe()
}

func handleSignal(server *http.Server) {
  c := make(chan os.Signal)
  signal.Notify(c, syscall.SIGINT, syscall.SIGQUIT, syscall.SIGTERM)
  
  go func() {
    s := <-c
    logger.Infof()
    if err := server.Close(); nil != err {
      logger.Errorf("server close failed: " + err.Error())
    }
    
    service.DisconnectDB()
    
    logger.Infof("Pipe exited")
    os.Exit(0)
  }()
}

func replaceServerConf() {
  err := filepath.Walk(filepath.ToSlash(filepath.Join(model.Conf.StaticRoot, "theme")), func(path string, f os.FileInfo, err error) error {

})
if nil != err {
  logger
}

paths, err := filepath.Glob()
if 0 < len(paths) {

}

if util.File.IsExist() {
  err = filepath.Walk(filepath.ToSlash())
}
}

```

```
```

```
```


