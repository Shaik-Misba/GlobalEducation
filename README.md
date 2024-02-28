**Student.java**
<p><code>
  @Entity
  @Table(name="student")
  public class Student{
        @Id
        @GeneratedValue(startegy=GenerationType.IDENTITY)
        Private Integer studentId;
    
        @Column(name="Country_interested")
        private String interestedCountry;
  }
</code></p>

ublic class Student DTO {

private Integer student Id

; @NotNull(message = "{student.studentname.notpresent}")

@Pattern(regexp = "([A-Za-z]+[ ]*)+", message = "(student.studentname.invalid}")

private String student Name;

@NotNull(message = "{student.emailid.notpresent}")

@Email(message = "(student.emailid.invalid}")

private String emailId;

@Not Null(message = "(student.country.not present}")

private String interestedCountry;

@NotNull(message = "{student. intakeyear.notpresent)")

private Integer intakeYear;

@Not Null(message = "{student.studylevel.notpresent}")

private String study Level;

@NotNull(message = "{student.course.notpresent}") private String courseInterested; 
