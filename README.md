# Medical-
Pharmacy shop management using vb.net and sql
Login form


Data.SqlClient
Imports System.Security.CryptographyImports System.Data
Imports System.
Imports System.Windows.Forms.VisualStyles.VisualStyleElement

Public Class Form1
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        Dim username As String = TextBox1.Text
        Dim password As String = TextBox2.Text

        Dim connectionString As String = "Data Source=DESKTOP-KTBHN7P\SQLEXPRESS;Initial Catalog=pharma;Integrated Security=True"
        Dim query As String = "SELECT COUNT(*) FROM t1 WHERE username = @username AND password= @password"

        Using connection As New SqlConnection(connectionString)
            Using Command As New SqlCommand(query, connection)

                Command.Parameters.AddWithValue("@username", username)
                Command.Parameters.AddWithValue("@password", password)
                connection.Open()
                Dim count As Integer = Convert.ToInt32(Command.ExecuteScalar())

                If count > 0 Then
                    Dim Form2 As New Form2()
                    Form2.Show()
                    Me.Hide()
                Else
                    MessageBox.Show("invalid credentials ")
                End If
            End Using
        End Using
    End Sub

    Private Sub TextBox1_TextChanged(sender As Object, e As EventArgs) Handles TextBox1.TextChanged
    End Sub

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
    End Sub

    Private Sub Label6_Click(sender As Object, e As EventArgs) Handles Label6.Click
    Form2.Show()
    End Sub
End Class
