## GraduateStudent
```
package com.saveetha.universitymanagement;

public class GraduateStudent extends Student {

    public GraduateStudent(int studentId, String lastName) {
        super(studentId, lastName);
        setTuition();
    }

    @Override
    public void setTuition() {
        setAnnualTuition(6000 * 2); // Assuming two semesters per year
    }
}
```
## Student.java
```
package com.saveetha.universitymanagement;

public abstract class Student {
    private int studentId;
    private String lastName;
    private double annualTuition;

    public Student(int studentId, String lastName) {
        this.studentId = studentId;
        this.lastName = lastName;
    }

    public int getStudentId() {
        return studentId;
    }

    public void setStudentId(int studentId) {
        this.studentId = studentId;
    }

    public String getLastName() {
        return lastName;
    }

    public void setLastName(String lastName) {
        this.lastName = lastName;
    }

    public double getAnnualTuition() {
        return annualTuition;
    }

    public void setAnnualTuition(double annualTuition) {
        this.annualTuition = annualTuition;
    }

    public abstract void setTuition();
}
```
## StudentAtLarge.java
```
package com.saveetha.universitymanagement;

public class StudentAtLarge extends Student {

    public StudentAtLarge(int studentId, String lastName) {
        super(studentId, lastName);
        setTuition();
    }

    @Override
    public void setTuition() {
        setAnnualTuition(2000 * 2); // Assuming two semesters per year
    }
}
```
## StdeuntController.java
```
package com.saveetha.universitymanagement;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.ArrayList;
import java.util.List;

@RestController
//@RequestMapping("/api/students")
public class StudentController {

    @GetMapping
    public List<Student> getStudents() {
        List<Student> students = new ArrayList<>();
        students.add(new UndergraduateStudent(1, "Smith"));
        students.add(new UndergraduateStudent(2, "Johnson"));
        students.add(new GraduateStudent(3, "Williams"));
        students.add(new GraduateStudent(4, "Jones"));
        students.add(new StudentAtLarge(5, "Brown"));
        students.add(new StudentAtLarge(6, "Davis"));

        return students;
    }
}

```
## UndergrauateStudent.java
```
package com.saveetha.universitymanagement;

public class UndergraduateStudent extends Student {

    public UndergraduateStudent(int studentId, String lastName) {
        super(studentId, lastName);
        setTuition();
    }

    @Override
    public void setTuition() {
        setAnnualTuition(4000 * 2); // Assuming two semesters per year
    }
}

```
## UniversityManagement.java
```
package com.saveetha.universitymanagement;

import org.springframework.boot.CommandLineRunner;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.Bean;

@SpringBootApplication
public class UniversityManagementApplication {

	public static void main(String[] args) {
		SpringApplication.run(UniversityManagementApplication.class, args);
	}

	@Bean
	public CommandLineRunner commandLineRunner(ApplicationContext ctx) {
		return args -> {
			Student[] students = new Student[6];

			students[0] = new UndergraduateStudent(1, "Smith");
			students[1] = new UndergraduateStudent(2, "Johnson");
			students[2] = new GraduateStudent(3, "Williams");
			students[3] = new GraduateStudent(4, "Jones");
			students[4] = new StudentAtLarge(5, "Brown");
			students[5] = new StudentAtLarge(6, "Davis");

			for (Student student : students) {
				System.out.println("Student ID: " + student.getStudentId() +
						", Last Name: " + student.getLastName() +
						", Annual Tuition: $" + student.getAnnualTuition());
			}
		};
	}
}

```
### Output
![Screenshot (105)](https://github.com/user-attachments/assets/1c2457ed-0a60-410f-afd6-441b64d84dcd)



