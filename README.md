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
		private Student Repository student Repository;

		public Student DTO registerStudent (Student DTO student DTO) throws GlobalEducationException { 
  			Student Validator.validate Student (student DTO);
			Optional<*Student> op=student Repository.findByEmailId(studentDTO.getEmailId()); 
   			if(op.isPresent()) {
      				throw new Global EducationException("Student Service. STUDENT_ALREADY_EXISTS");
			}
   			Student st=new Student();
      			st=Student DTO.prepareEntity(student DTO);
			Student snew-student Repository.save(st);
			st.setStudent Id (snew.get StudentId()); Student DTO sdt o=Student DTO.prepareDTO(st);
			return sdto;
		}
		public List<*Student DTO> get StudentByCountryAndIntake(String country, Integer intakeYear){
  			List<*Student> slist=studentRepository.findByInterestedCountryAndIntakeYear(country,intakeYear);
     			if(slist.isEmpty()){
				thow new GlobalEducationException("StudentService.NO_STUDENTS_FOUND");
    			}
       			List<*StudentDTO> dlist=new ArrayList<*StudentDTO>();
	  		for(Student student:slist) {
     				StudentDTO sdto=StudnetDTO.prepareDTO(student);
	 			dlist.add(sdto);
     			}
			Collections.sort(dlist.Comparator.comparing(StudentDTO::getStudentName));
   			return dlist;
      		}
     	}			
</code></p>

**ExceptionHandlerAdvice.java**
<p><code>
	@RestControllerAdvice
	public class ExceptionControllerAdvice{
		private static final log-------->
	
		@Autowired
  		private Environment environment;
    		@ExceptionHandler(globalEducationException.class)
      		public ResponseEntity<*ErrorInfo> globalEducationExceptionHandler(GlobalEducationException-){
			------------
		}

  		@exceptionHandler(Exception.class)
    		public ResponseEntity<*ErrorInfo> generalExceptionHnadler(Exception -){
      			-------
	 	}

   		@exceptionHandler({MathosArgumentNotValidException.class, ConstraintViolationException.class})
     		public ResponseEntity<*ErrorInfo> validatorExceptionHandler(Exception exception){
       			------------
	  	}
    }
</code></p>
