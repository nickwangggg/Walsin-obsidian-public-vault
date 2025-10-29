詳細介紹:
https://zamhuang.medium.com/rabbitmq-%E4%BA%94%E5%88%86%E9%90%98%E8%BC%95%E9%AC%86%E4%BA%86%E8%A7%A3-rabbitmq-%E9%81%8B%E4%BD%9C-fcaecbaa69d4

RabbitMQ其實是一種Message Queue
是**開源訊息代理（Message Broker）**，以 **AMQP 模型**（exchange→queue→consumer）為核心

Queue主要由三個元件所組成，
Producer(生產者)：主要用來發送訊息，訊息會透過Broker傳到Consumer
Consumer(消費者)：主要用來接收訊息，會從Broker去接收Producer傳來的訊息
Broker(佇列)：在Producer和Consumer之間扮演橋樑的角色，負責轉送訊息

![[../attachments/Pasted image 20251007130240.png]]

Queue的兩個最常見的用途，分別是任務緩衝、系統解耦

任務緩衝
譬如碰到有任務必須運算很久(CPU Bound的任務)，像用AI生成一張圖片要很長的時間，如果短時期碰到很多人想同時下載圖片，伺服器就有可能爆掉，也有些封包可能會遺失。Queue可以扮演了一個任務緩衝的角色，讓任務進行「排隊」，使得每個任務都不會遺失，排隊的使用者也可以先去做其他事(非同步任務)。

系統解耦
除此之外，Queue也可以幫助任兩個系統進行解耦，Producer和Consumer並不需要記得彼此的位址，只需要記得Queue在哪裡即可，如此三者可以架設在不同主機，也不需要使用相同語言開發，最重要是可以很方便依據需求對伺服器進行水平擴展(增加Server數量)。

舉例來說，原本Cient端要傳訊息交給Server端解決，但用戶數量突然增加，伺服器來不及處理完所有任務，由於Client端是向Queue傳遞訊息．可用增加Server數量取代增加Server效能，成本下降非常多，也大幅提高可擴充性。

