# ShoppingCart-with-Function
namespace pj
{
    public partial class Form1 : Form
    {
        public Form1()
        {
            InitializeComponent();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            // Initialize totals
            double totalFood = 0;
            double totalDrink = 0;
            double grandTotal = 0;

            // Get and process coffee price and quantity if "coffee" is selected
            try
            {
                if (coffee.Checked)
                {
                    double coffeePrice = double.Parse(tbCoffeePrice.Text);
                    double coffeeQuantity = double.Parse(tbCoffeeQuantity.Text);
                    totalDrink += coffeePrice * coffeeQuantity;
                }
            }
            catch (Exception)
            {
                MessageBox.Show("กรุณากรอกข้อมูลกาแฟให้ถูกต้อง");
            }

            // Get and process green tea price and quantity if "green tea" is selected
            try
            {
                if (grr.Checked)
                {
                    double greenTeaPrice = double.Parse(tbGreenCoffeePrice.Text);
                    double greenTeaQuantity = double.Parse(tbGreenCoffeeQuantity.Text);
                    totalDrink += greenTeaPrice * greenTeaQuantity;
                }
            }
            catch (Exception)
            {
                MessageBox.Show("กรุณากรอกข้อมูลชาเขียวให้ถูกต้อง");
            }

            // Get and process noodle price and quantity if "noodle" is selected
            try
            {
                if (noodle.Checked)
                {
                    double noodlePrice = double.Parse(tbNoodlePrice.Text);
                    double noodleQuantity = double.Parse(tbNoodleQuantity.Text);
                    totalFood += noodlePrice * noodleQuantity;
                }
            }
            catch (Exception)
            {
                MessageBox.Show("กรุณากรอกข้อมูลบะหมี่ให้ถูกต้อง");
            }

            // Get and process pizza price and quantity if "pizza" is selected
            try
            {
                if (pizza.Checked)
                {
                    double pizzaPrice = double.Parse(tbPizzaPrice.Text);
                    double pizzaQuantity = double.Parse(tbPizzaQuantity.Text);
                    totalFood += pizzaPrice * pizzaQuantity;
                }
            }
            catch (Exception)
            {
                MessageBox.Show("กรุณากรอกข้อมูลพิซซ่าให้ถูกต้อง");
            }

            // Calculate grand total
            grandTotal = totalFood + totalDrink;

            // Apply discount
            try
            {
                if (oo.Checked) // Apply discount to all
                {
                    double discountPercentage = double.Parse(tbDiscountAll.Text);
                    grandTotal -= grandTotal * (discountPercentage / 100);
                }
                else if (rbDiscountBeverage.Checked) // Apply discount to beverages only
                {
                    double discountPercentage = double.Parse(tbDiscountBeverage.Text);
                    totalDrink -= totalDrink * (discountPercentage / 100);
                    grandTotal = totalFood + totalDrink;
                }
                else if (rbDiscountFood.Checked) // Apply discount to food only
                {
                    double discountPercentage = double.Parse(tbDiscountFood.Text);
                    totalFood -= totalFood * (discountPercentage / 100);
                    grandTotal = totalFood + totalDrink;
                }
            }
            catch (Exception)
            {
                MessageBox.Show("กรุณากรอกข้อมูลส่วนลดให้ถูกต้อง");
            }

            // Display totals
            tbTotal.Text = grandTotal.ToString("F2");

            // Calculate change
            try
            {
                double cashReceived = double.Parse(tbCash.Text);

                if (cashReceived >= grandTotal)
                {
                    double change = cashReceived - grandTotal;
                    tbChange.Text = change.ToString("F2");

                    // Calculate denominations for change
                    int[] denominations = { 1000, 500, 100, 50, 20, 10, 5, 1 };
                    int remainingChange = (int)Math.Round(change);

                    foreach (int denom in denominations)
                    {
                        int count = remainingChange / denom;
                        remainingChange %= denom;

                        switch (denom)
                        {
                            case 1000:
                                tb1000.Text = count.ToString();
                                break;
                            case 500:
                                tb500.Text = count.ToString();
                                break;
                            case 100:
                                tb100.Text = count.ToString();
                                break;
                            case 50:
                                tb50.Text = count.ToString();
                                break;
                            case 20:
                                tb20.Text = count.ToString();
                                break;
                            case 10:
                                tb10.Text = count.ToString();
                                break;
                            case 5:
                                tb5.Text = count.ToString();
                                break;
                            case 1:
                                tb1.Text = count.ToString();
                                break;
                        }
                    }
                }
                else
                {
                    MessageBox.Show("เงินที่ได้รับไม่เพียงพอ");
                }
            }
            catch (Exception)
            {
                MessageBox.Show("กรุณากรอกจำนวนเงินที่ถูกต้อง");
            }
        }

        private void tbNoodlePrice_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)
        {

        }

        private void tbNoodleQuantity_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)
        {

        }

        private void tbPizzaPrice_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)
        {

        }

        private void tbPizzaQuantity_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)
        {

        }

        private void noodle_CheckedChanged(object sender, EventArgs e)
        {

        }

        private void discountFood_Enter(object sender, EventArgs e)
        {

        }

        private void pizza_CheckedChanged(object sender, EventArgs e)
        {

        }
    }
}
