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
〇　言語はJava (Spring.NETもあるが、ヒットしない)
---
〇　対象は主にWeb Application

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

〇　MVC

●　Spring MVC

HTTPとServletベースで、REST準拠WEBサービスの拡張も可能。

●　NablarchもHTTPとServletベースのMVCをサポート

+++?image=https://nablarch.github.io/docs/LATEST/doc/_images/web-design.png&size=80% 80%

---

〇DBアクセス機能


