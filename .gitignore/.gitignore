
using System;
using System.Drawing;
using System.Windows.Forms;

namespace WindowsFormsApplication2
{
    public partial class ang : Form
    {
        bool isMove = false;
        private Rectangle m_Rect;
        private Point m_LastMSPoint;

        public ang()
        {
            InitializeComponent();

            DoubleBuffered = true;
            this.SetStyle(ControlStyles.AllPaintingInWmPaint | ControlStyles.OptimizedDoubleBuffer | ControlStyles.UserPaint, true);
            m_Rect = new Rectangle(10, 10, 50, 30);
        }

        protected override void OnPaint(PaintEventArgs e)
        {
            e.Graphics.FillRectangle(SystemBrushes.ControlDark, this.m_Rect);
            e.Graphics.DrawRectangle(SystemPens.ControlDarkDark, this.m_Rect);

            //Rectangle r = e.ClipRectangle;
            //this.label1.Text = r.X + "," + r.Y;
        }

        protected override void OnMouseDown(MouseEventArgs e)
        {
            base.OnMouseDown(e);

            if (m_Rect.Contains(e.Location))
            {
                this.m_LastMSPoint = e.Location;

                isMove = true;//注意要加在这里
                Cursor = Cursors.SizeAll;
            }
            else
            {
                return;
            }
        }

        protected override void OnMouseMove(MouseEventArgs e)
        {
            base.OnMouseMove(e);

            if (e.Button != MouseButtons.Left)
            {
                return;
            }

            if (isMove == true)
            {
                this.label1.Text = m_LastMSPoint.X + "," + m_LastMSPoint.Y + " ; " + e.Location.X + "," + e.Location.Y;

                this.m_Rect.Offset(e.Location.X - this.m_LastMSPoint.X, e.Location.Y - this.m_LastMSPoint.Y);
                this.Invalidate();

                this.m_LastMSPoint = e.Location;
            }
        }

        protected override void OnMouseUp(MouseEventArgs e)
        {
            isMove = false;
            Cursor = Cursors.Default;
        }
    }
}
