
using System;
using System.Windows.Forms;

namespace Player1
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
            this.Load += Form1_Load; // Подключаем событие Load
        }
        private void Form1_Load(object sender, EventArgs e)
        {
            // Информация о типах short и float
            string shortInfo = $"short: [{short.MinValue} .. {short.MaxValue}], размер: {sizeof(short)} байт";
            string floatInfo = $"float: [{float.MinValue} .. {float.MaxValue}], размер: {sizeof(float)} байт";

            // Выводим в заголовок формы
            this.Text = $"Калькулятор (short, float): {shortInfo}; {floatInfo}";
        }

        private void label1_Click(object sender, EventArgs e)
        {

        }

        private void button1_Click(object sender, EventArgs e)
        {
            {
                short operand1 = short.Parse(txtOperand1.Text);
                float operand2 = float.Parse(txtOperand2.Text);
                string operation = txtOperation.Text;

                if (operation != "+" && operation != "-" && operation != "*" && operation != "/")
                {
                    MessageBox.Show("Поддерживаемые операции: +, -, *, /",
                        "Неверная операция", MessageBoxButtons.OK, MessageBoxIcon.Exclamation);
                    return;
                }

                var result = 0.0;
                switch (operation)
                {
                    case "+":
                        result = operand1 + operand2;
                        break;
                    case "-":
                        result = operand1 - operand2;
                        break;
                    case "*":
                        result = operand1 * operand2;
                        break;
                }
                lblResult.Text = $"Результат: {result:F6}";
            }
        }

        private void txtOperation_TextChanged(object sender, EventArgs e)
        {

        }
    }
}
