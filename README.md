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

**StudentDTO.java**
<p><code>
        private Integer student Id;
  
        @NotNull(message = "{student.studentname.notpresent}")
        @Pattern(regexp = "([A-Za-z]+[ ]*)+", message = "(student.studentname.invalid}")
        private String studentName;
        
        @NotNull(message = "{student.emailid.notpresent}")        
        @Email(message = "(student.emailid.invalid}")        
        private String emailId;
        
        @Not Null(message = "(student.country.not present}")
        private String interestedCountry;

        @NotNull(message = "{student.intakeyear.notpresent)")
        private Integer intakeYear;
        
        @Not Null(message = "{student.studylevel.notpresent}")
        private String studyLevel;
        
        @NotNull(message = "{student.course.notpresent}") 
        private String courseInterested; 
</code></p>

**StudentValidatory.java**
<p><code>
    public static void ValidateStudent(-------------------)
	{
 		if(!StudentValidatory.isValidIntakeYear(studentDTO.getIntakeYear())){
   			throw new GlobalEducatorException("StudnetValidator.INALID_INTAKE_YEAR");
	  }
   }
   public static Boolean isValidIntakeYear(Integer intakeYear){
	   	LocalDate ls=LocalDate.now();
		int year=ld.getYear();
	 	if(intakeYear>= year)
	  	{
	  		return true;
		}
	 	return false;
  }
        
</code></p>

**StudentRepository.java**
<p><code>
	public interface StudentRepository extends CrudRepository<*Student,Integer>	{
		public Optional<*Studnet> findByEmailId(String emailId);
		public Lidt<Studnet> findByInterestedCountryAndIntakeYear(String interestedCountry,Integer intakeYear);
</code></p>

**StudentAPI.java**
<p><code>
	@RestController
	@RequestMapping(value="global.edu")
	@Validated
	public class StudentAPI{
		@Autowired
		private StudentService studentService;

 		@PostMapping(value="student")
   		public ResponseEntity<*StudentDTO> registerStudent(---------------) {
		}

		@GetMapping(value="student/{country]/{intakeYear}")
  		public ResponseEntity<*List<*StudentDTO>> getStudentByCountryAndIntake(-----------){
		}
  }
</code></p>

**StudentServiceImpl.java**
<p><code>
	@Service(value="studentService")
	@Transactional
	public class StudentServiceImpl{
		@Autowored
		
</code></p>
