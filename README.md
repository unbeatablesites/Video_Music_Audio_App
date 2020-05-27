# Video_Music_Audio_App
An app that can play a video and allow the user to record audio. As a tool to assist in distance learning. 

This article shows you how to stream MP4 video in Spring Boot web application 
User Interface 


Project Structure


Home Controller
@Controller
public class HomeController {
 @Autowired
 private MyResourceHttpRequestHandler handler;
 private final static File MP4_FILE = new File("D:\\videofiles\\video1.mp4");
 // supports byte-range requests
 @GetMapping("/index")
 public String home() {
  return "index";
 }
 // supports byte-range requests
 @GetMapping("/byterange")
 public void byterange( HttpServletRequest request, HttpServletResponse response)
   throws ServletException, IOException {
  request.setAttribute(MyResourceHttpRequestHandler.ATTR_FILE, MP4_FILE);
  handler.handleRequest(request, response);
 }}
Spring Boot 
@SpringBootApplication
@ComponentScan({ "com" })
public class KnowledgefactorydemoApplication {
 public static void main(String[] args) {
  SpringApplication.run(KnowledgefactorydemoApplication.class, args);
 }}
MyResource HttpRequestHandler
@Component
public class MyResource HttpRequestHandler extends ResourceHttpRequestHandler { 
 final static String ATTR_FILE = MyResourceHttpRequestHandler.class.getName() + ".file";
 @Override protected Resource getResource(HttpServletRequest request) throws IOException {
  final File file = (File) request.getAttribute(ATTR_FILE);  return new FileSystemResource(file); }}
view (index.ftl)
<div class="row align-items-center justify-content-center">
                        <video width="1000" height="400" controls>
       <source src="byterange" type="video/mp4">
      </video>
</div>
