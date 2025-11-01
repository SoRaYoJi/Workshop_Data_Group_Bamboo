# Brazilian E-Commerce Public Dataset by Olist

## About Dataset  
Welcome! This is a Brazilian ecommerce public dataset of orders made at Olist Store. The dataset has information of 100k orders from 2016 to 2018 made at multiple marketplaces in Brazil. Its features allows viewing an order from multiple dimensions: from order status, price, payment and freight performance to customer location, product attributes and finally reviews written by customers. We also released a geolocation dataset that relates Brazilian zip codes to lat/lng coordinates.

This is real commercial data, it has been anonymised, and references to the companies and partners in the review text have been replaced with the names of Game of Thrones great houses.

## Join it With the Marketing Funnel by Olist  
We have also released a Marketing Funnel Dataset. You may join both datasets and see an order from Marketing perspective now!

Instructions on joining are available on this Kernel.

## Context  
This dataset was generously provided by Olist, the largest department store in Brazilian marketplaces. Olist connects small businesses from all over Brazil to channels without hassle and with a single contract. Those merchants are able to sell their products through the Olist Store and ship them directly to the customers using Olist logistics partners. See more on our website: www.olist.com

After a customer purchases the product from Olist Store a seller gets notified to fulfill that order. Once the customer receives the product, or the estimated delivery date is due, the customer gets a satisfaction survey by email where he can give a note for the purchase experience and write down some comments.

## Attention  
An order might have multiple items.  
Each item might be fulfilled by a distinct seller.  
All text identifying stores and partners where replaced by the names of Game of Thrones great houses.  

Example of a product listing on a marketplace  
Example of a product listing on a marketplace  

## Data Schema  
The data is divided in multiple datasets for better understanding and organization. Please refer to the following data schema when working with it:  
Data Schema
<img width="2486" height="1496" alt="image" src="https://github.com/user-attachments/assets/0eead964-b4e8-44ba-b9b0-f1d38255f4d7" />


## Classified Dataset  
We had previously released a classified dataset, but we removed it at Version 6. We intend to release it again as a new dataset with a new data schema. While we don't finish it, you may use the classified dataset available at the Version 5 or previous.

## Inspiration  
Here are some inspiration for possible outcomes from this dataset.

### NLP  
This dataset offers a supreme environment to parse out the reviews text through its multiple dimensions.

### Clustering  
Some customers didn't write a review. But why are they happy or mad?

### Sales Prediction  
With purchase date information you'll be able to predict future sales.

### Delivery Performance  
You will also be able to work through delivery performance and find ways to optimize delivery times.

### Product Quality  
Enjoy yourself discovering the products categories that are more prone to customer insatisfaction.

### Feature Engineering  
Create features from this rich dataset or attach some external public information to it.

## Acknowledgements  
Thanks to Olist for releasing this dataset.




# ชุดข้อมูลอีคอมเมิร์ซบราซิลโดย Olist (ฉบับแปลไทย)

## เกี่ยวกับชุดข้อมูล  
ยินดีต้อนรับ! นี่คือชุดข้อมูลอีคอมเมิร์ซสาธารณะของบราซิลที่รวบรวมคำสั่งซื้อจาก Olist Store ชุดข้อมูลนี้มีข้อมูลคำสั่งซื้อ 100,000 รายการตั้งแต่ปี 2016 ถึง 2018 ที่เกิดขึ้นในตลาดกลางหลายแห่งในบราซิล คุณลักษณะของข้อมูลช่วยให้สามารถดูคำสั่งซื้อได้จากหลายมิติ: ตั้งแต่สถานะคำสั่งซื้อ, ราคา, การชำระเงิน และประสิทธิภาพการขนส่ง ไปจนถึงตำแหน่งของลูกค้า, คุณลักษณะของผลิตภัณฑ์ และสุดท้ายคือรีวิวที่เขียนโดยลูกค้า เรายังได้เผยแพร่ชุดข้อมูลตำแหน่งทางภูมิศาสตร์ (geolocation dataset) ที่เชื่อมโยงรหัสไปรษณีย์ของบราซิลเข้ากับพิกัดละติจูด/ลองจิจูด

นี่คือข้อมูลเชิงพาณิชย์จริง ซึ่งถูกทำให้เป็นนิรนาม และการอ้างอิงถึงบริษัทและพันธมิตรในข้อความรีวิวได้ถูกแทนที่ด้วยชื่อตระกูลใหญ่จาก Game of Thrones

## เชื่อมต่อกับชุดข้อมูล Marketing Funnel โดย Olist  
เราได้เผยแพร่ชุดข้อมูล Marketing Funnel ด้วยเช่นกัน คุณสามารถเชื่อมต่อทั้งสองชุดข้อมูลและดูคำสั่งซื้อจากมุมมองทางการตลาดได้แล้ว!

คำแนะนำในการเชื่อมต่อมีอยู่ใน Kernel นี้

## บริบทของข้อมูล  
ชุดข้อมูลนี้ได้รับการสนับสนุนจาก Olist ซึ่งเป็นห้างสรรพสินค้าที่ใหญ่ที่สุดในตลาดกลางของบราซิล Olist เชื่อมโยงธุรกิจขนาดเล็กจากทั่วบราซิลเข้ากับช่องทางต่างๆ โดยไม่มีความยุ่งยากและผ่านสัญญาเดียว ผู้ค้าเหล่านั้นสามารถขายผลิตภัณฑ์ของตนผ่าน Olist Store และจัดส่งโดยตรงไปยังลูกค้าโดยใช้พันธมิตรด้านโลจิสติกส์ของ Olist ดูเพิ่มเติมได้ที่เว็บไซต์ของเรา: www.olist.com

หลังจากที่ลูกค้าซื้อผลิตภัณฑ์จาก Olist Store ผู้ขายจะได้รับการแจ้งเตือนเพื่อดำเนินการตามคำสั่งซื้อนั้น เมื่อลูกค้าได้รับสินค้า หรือถึงวันกำหนดส่งมอบสินค้าโดยประมาณ ลูกค้าจะได้รับแบบสำรวจความพึงพอใจทางอีเมล ซึ่งพวกเขาสามารถให้คะแนนประสบการณ์การซื้อ และเขียนความคิดเห็นบางอย่างได้

## ข้อควรทราบ  
หนึ่งคำสั่งซื้ออาจมีหลายรายการ  
แต่ละรายการอาจถูกดำเนินการโดยผู้ขายที่แตกต่างกัน  
ข้อความทั้งหมดที่ระบุร้านค้าและพันธมิตร ถูกแทนที่ด้วยชื่อตระกูลใหญ่จาก Game of Thrones  

ตัวอย่างรายการสินค้าบน marketplace  
ตัวอย่างรายการสินค้าบน marketplace  

## โครงสร้างข้อมูล  
ข้อมูลถูกแบ่งออกเป็นหลายชุดข้อมูลเพื่อความเข้าใจและการจัดระเบียบที่ดีขึ้น โปรดอ้างอิงโครงสร้างข้อมูลต่อไปนี้เมื่อทำงานกับมัน:  
Data Schema
<img width="2486" height="1496" alt="image" src="https://github.com/user-attachments/assets/94baff69-2a41-4a76-89a0-cdf0943725f6" />


## ชุดข้อมูลแบบจัดประเภท (Classified Dataset)  
ก่อนหน้านี้เราเคยเผยแพร่ชุดข้อมูลที่ถูกจัดประเภท แต่เราได้ลบออกไปในเวอร์ชัน 6 เราตั้งใจที่จะเผยแพร่ข้อมูลนี้อีกครั้งในรูปแบบชุดข้อมูลใหม่พร้อมโครงสร้างข้อมูลใหม่ ในระหว่างที่เรายังดำเนินการไม่เสร็จ คุณอาจใช้ชุดข้อมูลที่ถูกจัดประเภทที่มีอยู่ในเวอร์ชัน 5 หรือก่อนหน้าได้

## แรงบันดาลใจ  
นี่คือแรงบันดาลใจบางส่วนสำหรับผลลัพธ์ที่เป็นไปได้จากชุดข้อมูลนี้

### NLP  
ชุดข้อมูลนี้นำเสนอสภาพแวดล้อมที่ยอดเยี่ยมในการวิเคราะห์ข้อความรีวิวผ่านมิติต่างๆ

### การจัดกลุ่ม (Clustering)  
ลูกค้าบางคนไม่ได้เขียนรีวิว แต่ทำไมพวกเขาถึงมีความสุขหรือโกรธ?

### การพยากรณ์ยอดขาย (Sales Prediction)  
ด้วยข้อมูลวันที่ซื้อ คุณจะสามารถคาดการณ์ยอดขายในอนาคตได้

### ประสิทธิภาพการจัดส่ง (Delivery Performance)  
คุณสามารถวิเคราะห์ประสิทธิภาพการจัดส่งและค้นหาวิธีเพิ่มประสิทธิภาพเวลาการจัดส่งได้

### คุณภาพสินค้า (Product Quality)  
สนุกกับการค้นหาหมวดหมู่สินค้าที่มีแนวโน้มทำให้ลูกค้าไม่พึงพอใจ

### การสร้างฟีเจอร์ (Feature Engineering)  
สร้างคุณลักษณะจากชุดข้อมูลที่ครบถ้วนนี้ หรือเพิ่มข้อมูลสาธารณะภายนอกเข้ามาเสริม

## กิตติกรรมประกาศ  
ขอขอบคุณ Olist สำหรับการเผยแพร่ชุดข้อมูลนี้

dataset แหล่งข้อมูล https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/data?select=olist_customers_dataset.csv

