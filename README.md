using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.IO;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace StudentsManagement
{
    public partial class Students_Management_Program : Form
    {
        public bool loadCompleted_ = false;

        public Students_Management_Program()
        {
            InitializeComponent();
            InitVariables();
        }

        private void InitVariables()
        {
            ComboBox1_Gender.Items.Clear();
            ComboBox1_Gender.Items.Add("남자");
            ComboBox1_Gender.Items.Add("여자");

            ComboBox2_Gender.Items.Clear();
            ComboBox2_Gender.Items.Add("남자");
            ComboBox2_Gender.Items.Add("여자");

            ComboBox3_Gender.Items.Clear();
            ComboBox3_Gender.Items.Add("남자");
            ComboBox3_Gender.Items.Add("여자");

            ComboBox1_Gender.SelectedIndex = 0;
            ComboBox2_Gender.SelectedIndex = 0;
            ComboBox3_Gender.SelectedIndex = 0;
        }

        private void Load_Students_Info_Click(object sender, EventArgs e)
        {
            Load_Student();
            loadCompleted_ = true;
        }

        private void Load_Student() {
            StreamReader sr1 = new StreamReader(new FileStream("student1.dat", FileMode.Open));
            TextBox1_Name.Text = sr1.ReadLine();
            TextBox1_ID.Text = sr1.ReadLine();
            ComboBox1_Gender.Text = sr1.ReadLine();

            sr1.Close();

            StreamReader sr2 = new StreamReader(new FileStream("student2.dat", FileMode.Open));
            TextBox2_Name.Text = sr2.ReadLine();
            TextBox2_ID.Text = sr2.ReadLine();
            ComboBox2_Gender.Text = sr2.ReadLine();

            sr2.Close();

            StreamReader sr3 = new StreamReader(new FileStream("student3.dat", FileMode.Open));
            TextBox3_Name.Text = sr3.ReadLine();
            TextBox3_ID.Text = sr3.ReadLine();
            ComboBox3_Gender.Text = sr3.ReadLine();

            sr3.Close();
        }

        private void SaveButton1_Click(object sender, EventArgs e)
        {
            StreamWriter sw = new StreamWriter(new FileStream("student1.dat", FileMode.Create));
            sw.WriteLine(TextBox1_Name.Text);
            sw.WriteLine(TextBox1_ID.Text);
            sw.WriteLine(ComboBox1_Gender.Text);

            sw.Close();

            MessageBox.Show("학생 1 저장 완료", "확인");
        }

        private void SaveButton2_Click(object sender, EventArgs e)
        {
            StreamWriter sw = new StreamWriter(new FileStream("student2.dat", FileMode.Create));
            sw.WriteLine(TextBox2_Name.Text);
            sw.WriteLine(TextBox2_ID.Text);
            sw.WriteLine(ComboBox2_Gender.Text);

            sw.Close();

            MessageBox.Show("학생 2 저장 완료", "확인");
        }
        private void SaveButton3_Click(object sender, EventArgs e)
        {
            StreamWriter sw = new StreamWriter(new FileStream("student3.dat", FileMode.Create));
            sw.WriteLine(TextBox3_Name.Text);
            sw.WriteLine(TextBox3_ID.Text);
            sw.WriteLine(ComboBox3_Gender.Text);

            sw.Close();

            MessageBox.Show("학생 3 저장 완료", "확인");
        }
    }
}
