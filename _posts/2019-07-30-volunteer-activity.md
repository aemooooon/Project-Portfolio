---
layout: post
title: Volunteer Activity
feature-img: "assets/img/portfolio/cabin.png"
img: "assets/img/portfolio/cabin.png"
tags: [project 1, volunteer activity]
date: 2019-07-30
color: brown
---

From Student Moodle center, I found the External engagement and professional development. Adon encourages us to do IT-related volunteering which is individual professional development activities. Not only can we enrich our project experience, but it can also increase our value in our resume.


![alt text](https://github.com/aemooooon/app/blob/master/assets/img/p/014.png?raw=true "Volunteer Apply Mail")


For me, I should go to do more volunteer activities. Compared with my professional skills and abilities, I should improve my English listening, speaking, reading and writing skills. Because once I apply for a job after graduation, the bottom line is that I must be able to communicate and communicate with my future colleagues in an accurate and fluent manner. 

So I have to do it forwardly.

For the second year in my BIT, I was a Peer tutor at the Polytech.  helping some low level students improve their programming abilities. I think I am good at programming.

Just in the classroom of the database 3, Krissy wood said that the programming 1 class needs volunteer tutors to help the net students to try programming, because this year I heard that there are some real newbies. 

So I took the initiative to send Krissi Wood an email and applied for it. I think this is a very good opportunity to communicate with them. Although I don't completly understand English, I know C#, so I believe I must have no problem. 

I also thank Krissi for his support of my volunteer activities.

July 30, 2019. Today is the first time I have volunteered. There are more than a dozen students, so I am still getting some nervous, mainly because there is no confidence.

I took my textbook which used 2 years ago and sat in the last row. 
Listen to Krissi with other students to explain the new lab. After the end, everyone started to practice, do the lab. I turned around the classroom to see who needed help or hands up. 

Krissi also gave me a new book because some of it has been updated. 
During the period, almost five or six students hands up and asked me questions. 

Because of the current basic knowledge such as syntax, input and output, the use of simple operators. So even if I didn't understand it, I can see their problems at a glance. 

So this makes my job easier. I am still very enjoyable. Thank you.

### update
__Aug 6, 2019.__ Today Krissi talked about if else statements. I feel like all concept for new programmer is not hard to understand. Every one kind of smart, but the problems is then did not create a programming pattern inside of their brain. So I think they need memorize the all basic stuff.

__Aug 13, 2019.__ Today the topic was switch statements. Once again, everyone understand what the lecturer said but they still do not know how can start the lab. Most of the students put the semi clone everywhere. Hi, gusy , you need try, try ,try more...

__Aug 20, 2019.__ Today Krissi taught the do while loop. After that I help them to do practise lab. The most students did the Number Guessing game like generate a random number then let user guess what the number is, the game could feedback the number either too high or too low until they got correct result. I remember this do while loop in that situiation will using in assignment. So I had talked too much to student who was really entreisting the thing.

__Aug 27, 2019.__ I had taken a day off because of my ADS assignment.

__Sep 3, 2019.__ Today was a normal tutor day just like all other day but there was a intresting thing I would take a record. There is a lab called super challenge which is accept a sentence from user typing and show the stats result should like below:
```bash
Enter a sentence
The quick brown fox JUMPED OVER THE LAZY DOG
A1
B0
C0
D2
E3
F0
G1
H1
...
a0
b1
c1
d0
e1
f1
g0
h1
...
```

Because we can only use C Sharp array data type to implement it without hashtable or python dictionary. So eventhough I am a third year student of BIT, I am still not confident make a perfect eleganc code to do that, but finally the solution like below, just record here in case:
```c#
static void Main()
{
    string phrase;
    string lowerLetters = "abcdefghijklmnopqrstuvwxyz";
    string upperLetters = lowerLetters.ToUpper();
    int [] letterCountLower = new int[26];
    int [] letterCountUpper = new int[26];
    Console.Write("Enter a sentence: ");
    phrase = Console.ReadLine();
    
    foreach (char c in phrase)
    {
        if (upperLetters.Contains(c.ToString()))
        {
            letterCountUpper[upperLetters.IndexOf(c)] += 1;
        }
        else if (lowerLetters.Contains(c.ToString()))
        {
            letterCountLower[lowerLetters.IndexOf(c)] += 1;
        }
    }

    foreach (char c in lowerLetters)
    {
        Console.WriteLine(c + " " + letterCountLower[lowerLetters.IndexOf(c)]);
    }
    
    foreach (char c in upperLetters)
    {
        Console.WriteLine(c + " " + letterCountUpper[upperLetters.IndexOf[c]]);
    }

    Console.ReadLine();
}
```

__Sep 10, 2019.__ review for exam.

__Sep 17, 2019.__ review for exam.

__Sep 24, 2019.__ Today we talked about Method as well as taught the Swap algorithm. Krissi picked up four students includes me stand up in front of the room, each one of us hands up a paper which writes a number on, and when her call one of us then change the paper also change the position. It was really vivid. After the speaking, everyone start do the labs. But I found a very interesting thing. Everyone used the static method, which is the static keyword, according to the example in the book. This remind me that the static method of water is particularly deep especially in C Sharp. I would tell thest students about instance associated. But how?

__Oct 15, 2019.__ Today the topic is about enumeration and struct Data Types. Nothing new, I thought that thest topic just for assignment prerequisit.

__Oct 22, 2019.__ Today likes a final review which put all piece of knowledges together. Students will create a struct and read each field of data from a txt file and put it to array, also to struct array. Then need search, edit one of the item. And display all of the items. I tried to do some code to some nice students below:
```c#
using System;
using System.IO;

namespace ConsoleApp1
{
    public struct Student
    {
        public string lastName;
        public string firstName;
        public string address;
        public int team;
    }

    public class Program
    {
        static void Main(string[] args)
        {
            Student[] students = readFile(@"./names2.txt");
            displayStudents(students);
            writeFile(students);
            Console.ReadLine();
        }

        public static Student[] readFile(string fileName)
        {
            StreamReader sr = new StreamReader(fileName);
            Random r = new Random();
            string[] tempStr = sr.ReadToEnd().Split('\r');
            Student[] students = new Student[tempStr.Length / 2];
            for (int i = 0; i < tempStr.Length; i += 2)
            {
                for (int j = i / 2; j < tempStr.Length / 2; j++)
                {
                    students[j].firstName = tempStr[i].Trim('\n');
                    students[j].lastName = tempStr[i + 1].Trim('\n');
                    students[j].address = "Dunedin";
                    students[j].team = r.Next(1, 5);
                }
            }
            return students;
        }

        public static void displayStudents(Student[] students)
        {
            Console.WriteLine("Team".PadRight(10) + "First Name".PadRight(15) + "Last Name".PadRight(25) + "Address".PadRight(37));
            for (int i = 0; i < students.Length; i++)
            {
                Console.WriteLine(students[i].team.ToString().PadRight(10) + students[i].firstName.PadRight(15) + students[i].lastName.PadRight(25) + students[i].address.PadRight(37));
            }
        }

        public static void writeFile(Student[] students)
        {
            StreamWriter sw = new StreamWriter(@"ourClass.txt");
            for (int i = 0; i < students.Length; i++)
            {
                sw.WriteLine($"{students[i].team}  {students[i].firstName}  {students[i].lastName}  {students[i].address}");
            }
            sw.Close();
        }
    }
}
```

![alt text](https://github.com/aemooooon/app/blob/master/assets/img/p/062.png?raw=true "Final letter")