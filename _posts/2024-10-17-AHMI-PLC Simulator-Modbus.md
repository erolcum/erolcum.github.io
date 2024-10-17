---
layout: post
title: AdvancedHMI - PLC Simulator - Modbus TCP
---
<br><br>
[Simon oyununu Youtube'dan izleyebilirsin..](https://youtu.be/EesMmNoHW90)
<br><br>

Diğer blog sayfamda [Do-more PLC Simulator ve AdvancedHMI](https://erolcum.blogspot.com/2023/04/do-more-simulator-advancedhmi-baglants.html) arasında nasıl bağlantı kurulduğundan bahsetmiştim. Programları da aynı blog sayfamdaki linklerden temin edebilirsin.

Garry, Kanada'da yaşayan saygı değer bir insan. İnsanlarla bilgisini paylaşan birine ancak saygı duyulur çünkü. AdvancedHMI kısaca AHMI'ı araştırırken, onun bir blog yazısında Simon game projesini gördüm ve ben de denemek istedim. Serinin [5. yazısıydı](https://accautomation.ca/building-a-plc-program-that-you-can-be-proud-of-part-5). Garry'nin [Youtube kanalında](https://www.youtube.com/watch?v=CHWee7V1ccE) da videosu mevcut. 

Do-more PLC Simülatör, gerçekten çok güçlü bir yazılım. Normalde AutomationDirect PLC için ladder programlama yazılımı ama dahili simülatör, Soft plc gibi çalışabiliyor. Modbus TCP ve modbus RTU'yu hem server, hem de client olarak destekliyor. 300MB civarında bir kurulum dosyası var. Yani bilgisayarı kasmıyor. Modbus TCP server veya slave olarak çalışması için hiçbir ayar yapmanıza gerek kalmıyor. Birçok PLC normalde bir ayar yapmadan modbus server olarak çalışır. Siemens S7-1200 için Tia Portal'da bir kod bloğu koymak gerekiyor. Bu projede PLC server olarak çalışırken, AHMI, modbus client veya master olarak çalışmaktadır. 

Bu yazı bitmedi devam edecek..


<br><br>

```vb
Private Sub PilotLight1_Click(sender As Object, e As EventArgs) Handles PilotLight1.Click 
     Console.Beep(415, 420) ' Green Light
End Sub

Private Sub PilotLight2_Click(sender As Object, e As EventArgs) Handles PilotLight2.Click 
     Console.Beep(310, 420) ' Red Light
End Sub

Private Sub PilotLight3_Click(sender As Object, e As EventArgs) Handles PilotLight3.Click 
     Console.Beep(252, 420) ' Yellow Light
End Sub

Private Sub PilotLight4_Click(sender As Object, e As EventArgs) Handles PilotLight4.Click 
     Console.Beep(209, 420) ' Blue Light
End Sub

Private Sub DataSubscriber1_DataChanged(sender As Object, e As Drivers.Common.PlcComEventArgs) Handles DataSubscriber1.DataChanged
    If DataSubscriber1.Value = "1" Then
       Console.Beep(415, 420) ' Green
    ElseIf DataSubscriber1.Value = "2" Then
       Console.Beep(310, 420) ' Red
    ElseIf DataSubscriber1.Value = "4" Then
       Console.Beep(252, 420) ' Yellow
    ElseIf DataSubscriber1.Value = "8" Then
       Console.Beep(209, 420) ' Blue
    ElseIf DataSubscriber1.Value = "10" Then
       Console.Beep(120, 1500) ' Losing Sound
    ElseIf DataSubscriber1.Value = "20" Then
       For x = 1 To 8
          Console.Beep(600, 90) ' Winning Sound
          Threading.Thread.Sleep(20)
       Next 'x
    End If
End Sub

Private Sub PictureBox1_DoubleClick(sender As Object, e As EventArgs) Handles PictureBox1.DoubleClick
    Close()
End Sub
```
<br><br>

