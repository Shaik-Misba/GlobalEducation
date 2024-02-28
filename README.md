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
