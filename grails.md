# grails について

## grails のインストール

1. 展開
2. 環境変数の設定
```
SET GRAILS_HOME=xxxx
SET PATH=%PATH%;%GRAILS_HOME%\bin
```

## grails アプリの作り方

### プロジェクト作成
`grails create-app <プロジェクト名>` でプロジェクトを作成する。
```
> grails create-app test
```

### grailsコンソール
```
> grails
```
初回起動時は各種jarをダウンロードするため時間がかかる

```
| Starting interactive mode...
| Enter a command name to run. Use TAB for completions:
grails>
```

### コントローラ作成
`create-controller <コントローラ名>` でコントローラを作成する。
```
grails> create-controller hello
```

```
| Created grails-app/controllers/test/HelloController.groovy
| Created src/test/groovy/test/HelloControllerSpec.groovy
```

```
package test

class HelloController {

    def index() { }
}
```

### コントローラ修正
コントローラの修正
```
package test

class HelloController {

    def index() {
      render 'Hello World!'
    }
}
```

### アプリケーションの起動

```
grails> run-app
```

```
| Running application...
Grails application runnning at http://localhost:8080 in environment: development
grails>
```

[http://localhost:8080/hello/](http://localhost:8080/hello/) にアクセス

### アプリケーションの終了

```
grails> stop-app
```

```
| Shutting down application...
| Application shutdown.
grails>
```

### Grails コンソールの終了

```
grails> exit
```

```
>
```

## その他

### 設定ファイル

設定ファイルは `grails-app\conf\application.groovy` に作成

```
sample.key='value'
```

設定ファイルからの設定の取得は以下
```groovy:application.groory
println grailsApplication.config.sample.key
```

### 実行環境の取得方法

```
import grails.util.environment

switch (Environment.current) {
  case DEVELOPMENT:
    println 'dev'
    break
  case TEST:
    println 'test'
    break
  case PRODUCTION:
    println 'prod'
    break
}
```

### 環境の設定方法

###### grails 標準の環境の場合
コマンドの前に環境を指定する。
環境が指定されない場合は `dev` が指定されたもの。

以下は war を作成する場合
```
grails> dev war
grails> test war
grails> prod war
```

###### grails 標準の環境ではない場合
```
grails> -Dgrails.env=uat war
```

### 画面からのパラメータの取得

コントローラクラスから `params` で操作可能

### grails コマンド

| コマンド名 | 説明 |
|:-----------|:-----|
| **war**                         | WAR ファイルを作成する |
| **assemble**                    | Creates a JAR or WAR archive for production deployment |
| **bug-report**                  | Creates a zip file that can be attached to issue reports for the current project |
| **clean**                       | Cleans a Grails application's compiled sources |
| **compile**                     | Compiles a Grails application |
| **console**                     | Runs the Grails interactive console |
| **create-command**              | Creates an Application Command |
| **create-controller**           | Creates a controller |
| **create-domain-class**         | Creates a Domain Class |
| **create-functional-test**      | Creates a Geb Functional Test |
| **create-integration-test**     | Creates an integration test |
| **create-interceptor**          | Creates an interceptor |
| **create-scaffold-controller**  | Creates a scaffolded controller |
| **create-script**               | Creates a Grails script |
| **create-service**              | Creates a Service |
| **create-taglib**               | Creates a Tag Library |
| **create-unit-test**            | Creates a unit test |
| **dependency-report**           | Prints out the Grails application's dependencies |
| **generate-all**                | Generates a controller that performs CRUD operations and the associated views |
| **generate-async-controller**   | Generates an asynchronous controller that performs CRUD operations |
| **generate-controller**         | Generates a controller that performs CRUD operations |
| **generate-views**              | Generates GSP views for the specified domain class |
| **gradle**                      | Allows running of Gradle tasks |
| **help**                        | Prints help information for a specific command |
| **install**                     | Installs a Grails application or plugin into the local Maven cache |
| **install-templates**           | Installs scaffolding templates that use f:all to render properties |
| **list-plugins**                | Lists available plugins from the Plugin Repository |
| **open**                        | Opens a file in the project |
| **plugin-info**                 | Prints information about the given plugin |
| **run-app**                     | Runs a Grails application |
| **run-command**                 | Executes Grails commands |
| **run-script**                  | Executes Groovy scripts in a Grails context |
| **shell**                       | Runs the Grails interactive shell |
| **stats**                       | Prints statistics about the project |
| **stop-app**                    | Stops the running Grails application |
| **test-app**                    | Runs the applications tests |
| **url-mappings-report**         | Prints out a report of the project's URL mappings |
