Nablarch vs Spring
---
Nablarchについて

Nablarch(ナブラーク)は、TISの豊富な基幹システム構築経験から得られたナレッジを集約したJavaアプリケーション開発/実行基盤です。
<a href="https://nablarch.github.io/docs/LATEST/doc/" target="_blank">https://nablarch.github.io/docs/LATEST/doc/</a>

---
![ALT](framework.png)

<span style="font-size:0.6em; align=left">
Nablarchアプリケーションフレームワークは、ウェブやバッチといった処理方式に合わせた実行制御基盤と、 データベースアクセスやバリデーションといった個別の機能を提供するライブラリから構成される。</span>

---
Springについて

Javaプラットフォーム向けのオープンソースアプリケーションフレームワークである。
<a href="https://ja.wikipedia.org/wiki/Spring_Framework" target="_blank">https://ja.wikipedia.org/wiki/Spring_Framework</a>


---?image=http://cdn.springtutorials.com/wp-content/uploads/2016/03/spring-overview-current.png&size=50% 80%

---

NablarchとSpringの共通点
---
### 〇　言語はJava (Spring.NETもあるが、ヒットしない)
---
### 〇　対象は主にWeb Application

---
Web Application以外でも対応：  
    ●　Web Service     
    ●　Batch Application
---
●　Web Service

・Nablarch

RESTfulウェブサービス（推奨）

HTTPメッセージング
<a href="https://nablarch.github.io/docs/LATEST/doc/application_framework/application_framework/web_service/index.html" target="_blank">https://nablarch.github.io/docs/LATEST/doc/application_framework/application_framework/web_service/index.html</a>

---
・Spring

RESTfulウェブサービス（推奨）

<a href="https://spring.io/guides/gs/producing-web-service/" target="_blank">SOAP web service</a>
---
●　Batch Application

・Nablarch

JSR352に準拠したバッチアプリケーション（推奨）

Nablarchバッチアプリケーション

<a href="https://nablarch.github.io/docs/LATEST/doc/application_framework/application_framework/batch/index.html" target="_blank">https://nablarch.github.io/docs/LATEST/doc/application_framework/application_framework/batch/index.html</a>

・Spring

<a href="http://projects.spring.io/spring-batch/" target="_blank">Spring Batch</a>

---

### 〇　MVC

●　<a href="https://nablarch.github.io/docs/LATEST/doc/application_framework/application_framework/web/architecture.html" target="_blank">NablarchもHTTPとServletベースのMVCをサポート</a>

---?image=https://nablarch.github.io/docs/LATEST/doc/_images/web-design.png&size=80% 80%

---

●　Spring MVC

HTTPとServletベースで、REST準拠WEBサービスの拡張も可能。（アノテーション設定）

<a href="https://docs.spring.io/spring/docs/current/spring-framework-reference/web.html" target="_blank">https://docs.spring.io/spring/docs/current/spring-framework-reference/web.html</a>

---

### 〇　DBアクセス機能

●　Nablarch

・データベースアクセス(JDBCラッパー)

・ユニバーサルDAO（推奨）
<a href="https://nablarch.github.io/docs/5u8/doc/application_framework/application_framework/libraries/database_management.html" target="_blank">https://nablarch.github.io/docs/5u8/doc/application_framework/application_framework/libraries/database_management.html</a>


●　Spring

・JDBC and DAO

・O/R mapping (JDO, JPA, Hibernate, iBatis)

---

### 〇　トランザクション管理、排他制御

●　Nablarch

・JdbcTransactionFactory 

       <!-- コンポーネントとしてJdbcTransactionFactoryを設定する -->
       <component class="nablarch.core.db.transaction.JdbcTransactionFactory">

  			<!-- アイソレーションレベル -->
  			<property name="isolationLevel" value="READ_COMMITTED" />

  			<!-- トランザクションタイムアウト秒数 -->
  			<property name="transactionTimeoutSec" value="15" />

		</component>

---
●　Spring

・プログラミングによるトランザクション管理

・宣言的トランザクション管理（@Transactional）

---

### 〇　Validation

●　Nablarch

・Java EE7のBean Validation(JSR349)に準拠したバリデーション機能 (Bean Validation)（推奨）

・Nablarch独自のバリデーション機能 (Nablarch Validation)

<a href="https://nablarch.github.io/docs/LATEST/doc/application_framework/application_framework/libraries/validation.html" target="_blank">https://nablarch.github.io/docs/LATEST/doc/application_framework/application_framework/libraries/validation.html</a>


●　Spring
・Java EE7のBean Validation(JSR349)に準拠したバリデーション機能 (Bean Validation)

・Custom Validator

---
### 〇　セッション管理

●　Nablarch
セッション変数の保存先は以下３つ

・DBストア

・HIDDENストア

・HTTPセッションストア


---?image=https://nablarch.github.io/docs/LATEST/doc/_images/session_store.png&size=80% 80%

---

1.セッション変数保存ハンドラ の往路処理で、クッキーから取得したセッションIDをもとに、セッションストアからセッション変数をロードする。

2.業務アクションから SessionUtil を通して、セッション変数に対する読み書きを行う。

3.セッション変数保存ハンドラ の復路処理で、セッション変数をセッションストアに保存する。

4.JSPで参照できるように、セッション変数をリクエストスコープに設定する。(既にリクエストスコープに同名の値が存在する場合は設定しない。)

---

●　Spring

・ユーザーセッションを管理するAPIとその実装（例えばRedis）を提供する

・HttpSession - アプリケーションコンテナ（例えばTomcat）のHttpSessionに仲介する形でその機能を置き換える。

・クラスターセッション - アプリケーションコンテナ固有の問題に縛られることなく、クラスタリングされたセッションをサポートすることができる

・複数セッション - 1つのブラウザで複数のユーザーセッションを管理することができる。

・RESTful API - RESTfulなAPIでも動作するようにセッションIDをHTTPヘッダで提供できる

・WebSocket - WebSocketでメッセージを受け取ったときもHttpSessionを有効にし続ける機能を提供する

<a href="https://projects.spring.io/spring-session/" target="_blank">https://projects.spring.io/spring-session/</a>

---

### 〇　ログ出力

●　Nablarch

ログ出力は、３つの処理から構成されており、それぞれの実装を差し替えることができる。
---?image=https://nablarch.github.io/docs/LATEST/doc/_images/log-structure.png&size=80% 80%



