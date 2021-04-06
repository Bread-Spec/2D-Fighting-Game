# SKIRMISH GAME

using System;
using System.Windows.Forms;

namespace Skirmish
{
    

    public partial class Game : Form
    {
        
        //Initializes Booleans
        bool isJumping = false;
        bool right;
        bool left;

        //Generates Random Number
        Random rnd = new Random();
        Random rndalt = new Random();

        public Game()
        {
            InitializeComponent();
        }

        //Initializes Character and Enemy Health;
        static int EnemyHealth = 10;
        static int CharacterHealth = 10;

        private void Game_Load(object sender, EventArgs e)
        {

        }

        private void Character1_Click(object sender, EventArgs e)
        {

        }

        //Initializes Gravity
        private void Gravity_Tick(object sender, EventArgs e)
        {
            //Character
            if (!Character1.Bounds.IntersectsWith(Ground.Bounds) && isJumping == false)
            {
                Character1.Top += 10;
                Stance2.Top += 10;
                Attack.Top += 10;
                Walk.Top += 10;
            }

            else if (Character1.Bounds.IntersectsWith(Ground.Bounds))
            {
                Stance2.Visible = false;
                Character1.Visible = true;
            }

            //Enemy
            if (!Enemy.Bounds.IntersectsWith(Ground.Bounds))
            {
                Enemy.Top += 10;
                EnemyAttack.Top += 10;
            }

        }

        //Jump Mechanic
        private void Jump_Tick(object sender, EventArgs e)
        {

            if (Character1.Top <= 0)
                return;

            if (isJumping == true)
            {

                Character1.Top -= 10;
                Stance2.Top -= 10;
                Attack.Top -= 10;
                Walk.Top -= 10;
            }
        }

        //Movement Mechanic
        private void Timer1_Tick(object sender, EventArgs e)
        {
            //Character
            if (right == true)
            {
                if (!Character1.Bounds.IntersectsWith(Enemy.Bounds))
                {
                    Character1.Left += 10;
                    Stance2.Left += 10;
                    Attack.Left += 10;
                    Walk.Left += 10;
                }

                if (Character1.Bounds.IntersectsWith(Border_Right.Bounds))
                {
                    Character1.Left -= 10;
                    Stance2.Left -= 10;
                    Attack.Left -= 10;
                    Walk.Left -= 10;
                }
            }

            else if (left == true)
            {
                Character1.Left -= 10;
                Stance2.Left -= 10;
                Attack.Left -= 10;
                Walk.Left -= 10;

                if (Character1.Bounds.IntersectsWith(Border_Left.Bounds))
                {
                    Character1.Left += 10;
                    Stance2.Left += 10;
                    Attack.Left += 10;
                    Walk.Left += 10;
 
