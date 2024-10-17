---
layout: post
title: AdvancedHMI-PLC Simulator-Modbus TCP
---



<br><br>

```vb
Private Sub PilotLight1_Click(sender As Object, e As EventArgs) Handles PilotLight1.Click ' Green Light
     Console.Beep(415, 420)
End Sub

Private Sub PilotLight2_Click(sender As Object, e As EventArgs) Handles PilotLight2.Click ' Red Light
     Console.Beep(310, 420)
End Sub

Private Sub PilotLight3_Click(sender As Object, e As EventArgs) Handles PilotLight3.Click ' Yellow Light
     Console.Beep(252, 420)
End Sub

Private Sub PilotLight4_Click(sender As Object, e As EventArgs) Handles PilotLight4.Click ‘ Blue Light
     Console.Beep(209, 420)
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

