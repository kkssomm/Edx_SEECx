# Programming Exercise 1

[페이지로 이동](https://courses.edx.org/courses/course-v1:TUMx+SEECx+1T2018/courseware/66ff53b993894fcea837c84de9a437dc/5d288f9bcff945828ed188aac9f921cc/3?activate_block_id=block-v1%3ATUMx%2BSEECx%2B1T2018%2Btype%40vertical%2Bblock%40b6a7f5a55615456a88fccebbf506b2ba)



*** Install and Configure Eclipse **

1. Java 8 JDK 다운로드 및 설치 [링크](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

2. Eclipse IDE for Java Developers 다운로드 및 설치 [링크](https://www.eclipse.org/downloads/eclipse-packages)

3. Eclipse를 기동시키고, Workspace를 선택한 후 Welcome Screen을 없앤다.

4. 다음과 같이 Git Repository에 있는 프로젝트를 Import한다.

   **File** --> **Import...** --> **Existing Projects into Workspace** --> Click **Browse...** next to **Select root directory**

   그리고 Git Repository의 위치를 선택한다.





### EXERCISE STEPS

1. "Launch Exercise" 를 클릭해 TUM Exercise Application 페이지로 이동한다.

2.  “Start Exercise” 를 클릭해 내 Repository를 생성한다.

3. 과제를 수행하기 위한 두 가지 방법:

4. 1) **하나:** **"Open Exercise" 버튼을 클릭해 Online code editor로 과제 수행** 

   온라인 에디터는 자동완성과 에러 하이라이팅을 제공하지 않으나, 셋업 할 필요가 없다. 

   2) **둘:** **"Clone Repository" 버튼을 클릭해 내 컴퓨터에 Clone 하기** 

   Source Tree, Eclipse 등 선호하는 IDE를 사용할 수 있다.

   - 간단한 구문을 작성하는 과제이므로 온라인 코드 에디터를 사용하기로 했다. Exercise를 위한 기본적인 파일들이 이미 생성되어 있었다.

   ![1568486628319](..\img\ex_03_01.png)

5. 테스트에 통과할 때까지 요구하는 작업을 수행한 코드를 Commit, Push한다. 마지막 제출만 카운트 되므로 여러 번 제출이 가능하다.





### PART 1: ENCAPSULATION

In the requirements of the University App we have identified FR2, which shows the need for a Course object:

> FR2: Check course details: A student can see details about a course such as the course times, the location of the lecture hall on a map and other course attendees including their name and picture.

**You have the following tasks:**

1. Course 클래스를 생성한다. Course 클래스는 다음과 같은 속성을 가지며, 모든 속성은 public으로 한다.

2. 1. **title**: Course name of type String
   2. **lecturer**: Object of type Lecturer
   3. **dates**: The course dates as a list of Date objects (List<Date>)
   4. **attendees**: A list of Student objects (List<Student>)
      ![img](..\img\ex_03_02.png)

3. String 타입의 **title**을 인자로 받는 **Course**생성자를 추가한다. 이 때 **Course** 객체의title 속성을 초기화 한다. 

4. 인자와 return 타입이 없는**printCourseTitle()** 메소드를 추가한다. System.out.println()을 사용해 Course의 title을 출력하도록 한다.

5. **main()** 메소드 내에 title은 "SEECx", date는 "2017-05-30 12:00" 을 갖는 Course 타입 객체를 추가한다. class Main에 존재하는 **course** 속성을 이용하라. 그리고 "SEECx" Course 객체의 printCourseTitle()을 호출한다.

6. **Optional exercise:** Lecturer와 student 객체를 생성하고 SEECx Course 객체를 참조한다.

- Course.java

  ```
  // TODO: Implement Course Class
  public class Course{
      public String title;
      public Lecturer lecturer;
      public List<Date> dates;
      public List<Student> attendees;
      
      public Course(String title){
          this.title = title;
      }
      
      public void printCourseTitle(){
          System.out.println(title);
      }
  }
  ```

- Main.java

  ```
  public class Main {
      // TODO: remove comment and instantiate Course object in main method
      public static Course course;
  
      public static void main(String[] args) throws MalformedURLException {
  
          Date seecxStartDate = new Date(2017,05,30,12,0);
          List<Date> seecxDates = new ArrayList<>(1);
          seecxDates.add(seecxStartDate);
  
          // TODO: instantiate course here
          // And invoke printCourseTitle()
          // Use seecxDates for the list of course dates
          course = new Course("SEECx");
          course.dates = seecxDates;
          course.printCourseTitle();
      }
  }
  ```

- submit

  ![1568494926395](C:\Users\user\AppData\Roaming\Typora\typora-user-images\1568494926395.png)

  - Submit 버튼을 누르면 어떤 항목이 채점되었는지 파악할 수 있다. Part1만 작성해 제출했을 때 16항목 중 10개만 맞게 채점되었다.





### PART 2: INHERITANCE

We want the University App to support *Online Courses* and *Lecture Courses*. There are few differences between them. Lecture courses take place in a lecture hall which has a location. Online courses however do not directly have a location. Instead, they have an URL where you can find the course material. To take this into account, we create subclasses of the Course class.

**You have the following tasks:**

1. Course 클래스를 extends 하는 subclass인**LectureCourse** 생성하고 다음 속성들을 포함하도록 한다:

2. - lecture의 x, y 좌표를 보관하는 Java Point 타입**location** 속성을 생성한다. 
   
   - String 타입의**title** 과 Point 타입의**location** 2가지 인자를 받는 생성자를 만들어 LectureCourse의 속성을 초기화한다.

   - main() 메소드 내에서  "POM"의 title, "100, 70"의 location을 갖는 LectureCourse 객체를 하나 선언한다. 이 때 **Main**클래스에 존재하는 **lectureCourse** 를 이용하라. 이 "POM" LectureCourse의 printCourseTitle()를 호출한다.
   
3. 또 다른 subclass인 **OnlineCourse**를 다음 속성들을 포함하도록 생성한다:

4. - Course의 url을 보관하는 Java URL 타입의 **url** 속성. 
   
   - String 타입의 **title** 과 URL 타입의**url** 2가지 인자를 받는 생성자.
   
   - main() 메소드 내에서 "SEECx"이라는 title,  "https://www.edx.org/course/software-engineering-essentials-tumx-seecx" 의 url을 갖는 **OnlineCourse** 객체를 하나 선언한다. 이 때 **Main** 클래스에 존재하는 **onlineCourse** 를 사용하라. "SEECx" onlineCourse 객체의 printCourseTitle()를 호출한다.

 ![img](https://studio.edge.edx.org/asset-v1:TUM+IN1504+2016+type@asset+block@OOP1Exercise_2.png)

- LectureCourse.java

  ```
  // TODO: Implement LectureCourse Class
  public class LectureCourse extends Course{
      public Point location;
      
      public LectureCourse(String title, Point location){
          super(title);
          this.location =location;
      }
  }
  ```

- OnlineCourse.java

  ```
  // TODO: Implement OnlineCourse Class
  public class OnlineCourse extends Course{
      public URL url;
      
      public OnlineCourse(String title, URL url){
          super(title);
          this.url = url;
      }
  }
  ```

  - java.awt.Point, java.net.URL을 import

- Main.java

  ```
  public class Main {
      // TODO: remove comment and instantiate LectureCourse object in main method
      public static LectureCourse lectureCourse;
      
      // TODO: remove comment and instantiate OnlineCourse object in main method
      public static OnlineCourse onlineCourse;
  
  
      public static void main(String[] args) throws MalformedURLException {
  
          Point pomLocation = new Point(100,70);
          
          // TODO: instantiate lectureCourse here
          // And invoke printCourseTitle()
          // Use pomLocation for the course location
          lectureCourse = new LectureCourse("POM",pomLocation);
  
  
          URL seecxUrl = new URL("https://www.edx.org/course/software-engineering-essentials-tumx-seecx");
          
          // TODO: instantiate onlineCourse here
          // And invoke printCourseTitle()
          // Use seecxUrl for the course URL
          onlineCourse = new OnlineCourse("SEECx",seecxUrl);
          onlineCourse.printCourseTitle();
      }
  }
  ```

- Submit

![1568528772643](..\img\ex_03_03.png)





### Results

![1568529081733](..\img\ex_03_04.png)

