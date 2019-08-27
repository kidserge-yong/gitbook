# Single-Responsibility Principle

## 👑 หัวใจหลักของ Single-Responsibility Principle \(SRP\)

> A class should have only one reason to change.

{% hint style="info" %}
คลาสในที่นี้ รวมถึง method หรือ module ด้วยนะ หรือ พูดรวมๆคือโค้ดทุกอย่างนั่นแหละ
{% endhint %}

เลยทำให้เราแปลออกมาได้ว่า **"Class, Method, หรือ Module ต่างๆนั้น ควรจะมีแค่เหตุผลเดียวในการแก้ไข"** นี่คือหัวใจของ SRP เลย หรือพูดง่ายๆอีกแบบว่า "ถ้าเราคิดเหตุผลที่จะทำให้เราต้องแก้โค๊ดกลุ่มนั้นๆได้มากกว่า 1 เหตุผลแล้วละก็ แสดงว่าผิดกฏของ SRP"

{% hint style="danger" %}
**SRP**  
เป็นหลักออกแบบตัวแรกที่ง่ายที่สุด แต่เป็นตัวที่เข้าใจและทำได้ยากที่สุดตัวนึง เพราะหลักตัวนี้มันไม่ได้อยู่แค่ที่โค๊ด แต่มันลงไปถึงระดับของ **คน** ซึ่งคนในที่นี้คือคนที่ทำให้เกิด **Requirement Change**
{% endhint %}

{% hint style="info" %}
**Requirement**  
คือสิ่งที่ลูกค้าต้องการ เช่นเวลาเราจะสร้างแอพออกมาซักตัว เราก็ต้องไปทำความเข้าใจก่อนว่าลูกค้าอยากจะได้แอพแบบไหน หรืออยากให้มันทำอะไรได้บ้าง
{% endhint %}

## ❓ ทำไมต้องมีแค่เหตุผลเดียว ?

ถ้าโค้ดที่รับผิดชอบงานนั้นๆ มีเหตุผลที่ทำให้เราต้องไปแก้มากกว่า 1 เหตุผล แสดงว่าโค้ดพวกนั้นมันดูแลงานมากกว่า 1 เรื่อง เมื่อเกิด **Requirement Change** เราต้องไปแก้โค้ด และถ้าโค้ดนั้นมีเรื่องที่มันดูแลมากกว่า 1 เรื่อง **เราจะมั่นใจได้ยังไงว่าเรื่องที่เราแก้จะไม่ไปกระทบกับอีกเรื่องที่มันไม่เกี่ยวข้องด้วย?** และ **จะมั่นใจได้ยังไงว่าเรื่องทั้ง 2 มันจะไม่ไปผูกกันโดยที่เราไม่ตั้งใจได้?**

## 👑 นิยามที่ 2 ของ SRP

หลังๆมาพ่อใหญ่ **Robert C.Marin** ก็พบว่าหลายๆคนอ่านแล้วเข้าใจในนิยามแรกแล้วเข้าใจผิดกันเยอะมาก แกเลยนิยามหลักการนี้เป็นตัวที่ 2 ออกมาว่า

> Gather together the things that change for the same reasons. Separate those things that change for different reasons.

ซึ่งแปลออกมาได้ว่า

> รวมของที่เกิดจาก requirement เดียวกันไปไว้ด้วยกัน และแยกของที่เกิดจากการเปลี่ยนแปลงจาก requirement อื่นไปรวมไว้ที่อื่น

เลยเป็นเหตุผลว่า **นิยามแรกมันไม่ได้จำกัดความเพียงแค่คลาสเท่านั้น** และมันต้องออกแบบโดยดูเนื้อหาของ **Requirement** ด้วย

## 😕 แล้วจะรู้ได้ยังไงว่าความรับผิดชอบมันดูจากไหน

สมมุติว่าเราเขียนโปรแกรมแล้วมีความต้องการเข้ามาจาก 2 ฝ่ายคือ **ความต้องการของฝ่ายการตลาด** กับ **ความต้องการของฝ่ายบัญชี** ซึ่งความต้องการของทั้ง 2 ฝ่ายนี้ในบางทีอาจจะเป็นเรื่องเดียวกันก็ได้ เช่น อยากได้หน้ารายงานแบบเดียวกันเป๊ะๆทั้ง 2 ฝ่าย เราก็เลยทำหน้ารายงานให้

### 😟 **การออกแบบที่ไม่ดี**

หน้ารายงานของทั้ง 2 ฝ่ายเราทำเป็นหน้าเดียวกัน เพราะทั้ง 2 ฝ่ายอยากได้แบบเดียวกันเป๊ะๆเลยนิน่า ก็ดูเหมือนจะไม่มีอะไรใช่ไหม แต่พอวันนึง**ฝ่ายบัญชี**อยากให้เพิ่มคอลัมน์เข้าไปในรายงานหน่อย เขาจะได้ดูผลสรุปได้ง่ายๆ พอเราแก้ให้เสร็จเขาก็ยิ้มสบายใจ แต่อีก 3 วันให้หลัง**ฝ่ายการตลาด**หน้ามุ่ยเดินถีบประตูมาหาเราทันที และโวยวายว่าทำไมรายงานมันมีคอลัมน์เพิ่มเข้ามาล่ะ ฝ่ายฉันไม่ได้อยากได้แบบนี้นะ! **นี่คือตัวอย่างที่ละเมิดกฏของ SRP**

{% hint style="danger" %}
**ข้อควรระวัง**  
จะเห็นว่าเรื่อง SRP มันไม่ได้ลงไปแค่ในระดับโค้ดเท่านั้น แต่มันจะครอบคลุมไปถึงระดับ requirement ด้วย เช่นความต้องการของ **Requirement Change จากกลุ่มเดียวกัน** ก็ต้องมีโค้ดชุดนึงดูแลรับผิดชอบแยกออกไป
{% endhint %}

### 😄 การออกแบบที่ควรเป็น

แทนที่เราจะทำหน้ารายงานเป็นหน้าเดียวกัน ให้เราแยกโค้ดและหน้ารายงานที่เหมือนกันเป๊ะๆออกเป็น 2 อัน แล้วพอ**ฝ่ายบัญชี**ขอแก้ไขการแสดงผลก็จะมีแค่โค้ดที่รับผิดชอบ Requirement change ของฝั่งบัญชีเท่านั้นที่ถูกแก้ไข ไม่มีผลกระทบกับโค้ดที่ดูแล Requirement change ของ**ฝ่ายการตลาด** และในทางกลับกันถ้า**ฝ่ายการตลาด**อยากเพิ่มอะไร มันก็จะไม่มีผลกระทบกับ**ฝ่ายบัญชี**เช่นกัน

{% hint style="danger" %}
**ข้อควรระวัง**  
**อย่าเมากาวเอา SRP ไปใช้แบบตะบี้ตะบัน** ไม่งั้นเราจะทำงานออกมาได้ช้ากว่าปรกติ เช่น ในเคสตัวอย่างนี้ถ้าทีมเราไม่มีกำลังคนเหลือจริงๆ การรวมรายงานเป็นหน้าเดียวกันแม้อาจจะทำให้เป็นผลดีกว่าไปเสียเวลาเพิ่มโค้ดก็ได้ \(แม้จะผิดหลัก SRP ก็ตาม\) ดังนั้นจะใช้ SRP ต้องชั่งน้ำหนักด้วยว่าควระทำถึงระดับไหนและเมื่อไหร่ควรที่จะทำ
{% endhint %}

### 💡 Fragile design

เป็นคำเรียกการออกแบบที่ไม่ดี เพราะโค๊ดพวกนั้นเปราะบางมาก เราไปแก้ไขมันหน่อยก็พัง มีคนมาเรียกใช้ส่งข้อมูลไปไม่ดีก็พัง ซึ่งเราควรจะหลีกเลี่ยงการออกแบบโค๊ดไม่ให้มันเปราะบาง \(กาก\) แบบนี้ให้มากที่สุด

{% hint style="info" %}
**Code smell**  
เป็นเทคนิกในการดูว่าโค๊ดเรามีปัญหาหรือไม่ และจะหลีกเลี้ยงมันยังไง \(ในอนาคตผมจะเขียนบทความเรื่อง code smell ไว้นะครับก็รอติดตามอ่านดูได้ที่สลัดผักนี่แหละ\)
{% endhint %}

## 🎥 วีดีโอเผื่ออยากเห็นตัวอย่างมากขึ้น

{% embed url="https://www.youtube.com/watch?v=26Vplc5LVGg&list=PLUjAn8nwWniiCUZtTOEHPWHw0WxpdH3DX&index=2" %}
