# Video_Music_Audio_App
An app that can play a video and allow the user to record audio. As a tool to assist in distance learning. 

<div class="post-body entry-content float-container" id="post-body-1323850920477583280">
<span style="font-family: Courier New, Courier, monospace;"><span style="background-color: white;">This article shows you how to stream MP4 video in Spring Boot web application&nbsp;</span></span><br>
<span style="font-family: Courier New, Courier, monospace;"><span style="background-color: white;"><b>User Interface</b>&nbsp;</span></span><br>
<div class="separator" style="clear: both; text-align: center;">
<a href="https://1.bp.blogspot.com/-Ugh0IlGUJVI/XYXvMq40EnI/AAAAAAAAAPk/i7adQobUlk8j5_KN3A0TmZSC4ix6GcyewCPcBGAYYCw/s1600/stream.PNG" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" data-original-height="322" data-original-width="660" height="310" src="https://1.bp.blogspot.com/-Ugh0IlGUJVI/XYXvMq40EnI/AAAAAAAAAPk/i7adQobUlk8j5_KN3A0TmZSC4ix6GcyewCPcBGAYYCw/s640/stream.PNG" width="640"></a></div>
<span style="font-family: Courier New, Courier, monospace;"><span style="background-color: white;"><br></span></span>
<span style="font-family: Courier New, Courier, monospace;"><span style="background-color: white;"><b>Project Structure</b></span></span><br>
<div class="separator" style="clear: both; text-align: center;">
<a href="https://1.bp.blogspot.com/-UE5LHWISssE/XYXvkfuNKuI/AAAAAAAAAPs/c7IIOKoPoRMsCyhujjNA6X5A4PWUYZA2gCPcBGAYYCw/s1600/structure.PNG" imageanchor="1" style="margin-left: 1em; margin-right: 1em;"><img border="0" data-original-height="391" data-original-width="342" height="320" src="https://1.bp.blogspot.com/-UE5LHWISssE/XYXvkfuNKuI/AAAAAAAAAPs/c7IIOKoPoRMsCyhujjNA6X5A4PWUYZA2gCPcBGAYYCw/s320/structure.PNG" width="279"></a></div>
<span style="font-family: Courier New, Courier, monospace;"><span style="background-color: white;"><b><br></b></span></span>
<span style="font-family: Courier New, Courier, monospace;"><span style="background-color: white;"><b>Home Controller</b></span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">@Controller</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">public class HomeController {</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;@Autowired</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;private MyResourceHttpRequestHandler handler;</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;private final static File MP4_FILE = new File("D:\\videofiles\\video1.mp4");</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;// supports byte-range requests</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;@GetMapping("/index")</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;public String home() {</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp; return "index";</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;}</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;// supports byte-range requests</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;@GetMapping("/byterange")</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;public void byterange( HttpServletRequest request, HttpServletResponse response)</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp; &nbsp;throws ServletException, IOException {</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp; request.setAttribute(MyResourceHttpRequestHandler.ATTR_FILE, MP4_FILE);</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp; handler.handleRequest(request, response);</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;}}</span></span><br>
<span style="font-family: Courier New, Courier, monospace;"><span style="background-color: white;"><b>Spring Boot&nbsp;</b></span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">@SpringBootApplication</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">@ComponentScan({ "com" })</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">public class KnowledgefactorydemoApplication {</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;public static void main(String[] args) {</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp; SpringApplication.run(KnowledgefactorydemoApplication.class, args);</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;}}</span></span><br>
<span style="font-family: Courier New, Courier, monospace;"><span style="background-color: white;"><b>MyResource HttpRequestHandler</b></span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">@Component</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">public class MyResource HttpRequestHandler extends ResourceHttpRequestHandler {&nbsp;</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;final static String ATTR_FILE = MyResourceHttpRequestHandler.class.getName() + ".file";</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp;@Override protected Resource getResource(HttpServletRequest request) throws IOException {</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp; final File file = (File) request.getAttribute(ATTR_FILE);&nbsp; return new FileSystemResource(file); }}</span></span><br>
<span style="font-family: Courier New, Courier, monospace;"><span style="background-color: white;"><b>view (index.ftl)</b></span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&lt;div class="row align-items-center justify-content-center"&gt;</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &lt;video width="1000" height="400" controls&gt;</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp; &nbsp; &nbsp; &nbsp;&lt;source src="byterange" type="video/mp4"&gt;</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&nbsp; &nbsp; &nbsp; &lt;/video&gt;</span></span><br>
<span style="color: #741b47; font-family: Courier New, Courier, monospace;"><span style="background-color: white;">&lt;/div&gt;</span></span><br>
<div style="text-align: center;">
<span style="font-family: Courier New, Courier, monospace;"><span style="background-color: white;">$ git clone&nbsp;&nbsp;</span></span></div>
<div style="text-align: center;">
<span style="font-family: Courier New, Courier, monospace;"><span style="background-color: white;"><a href="https://github.com/knowledgefactory4u/KnowledgeFactory">https://github.com/knowledgefactory4u/KnowledgeFactory</a></span></span></div>
<div>
<div>
<div style="font-family: arial, tahoma, helvetica, freesans, sans-serif; margin: 0px; position: relative;">
</div>
</div>
<span style="background-color: white;"><span style="font-family: &quot;trebuchet ms&quot; , sans-serif;">
</span></span>
<br>
<div>
<br></div>
<span style="background-color: white;"><span style="font-family: &quot;trebuchet ms&quot; , sans-serif;">
</span></span>
<br>
<div class="separator" style="clear: both; text-align: center;">
<span style="background-color: white;"><span style="font-family: &quot;trebuchet ms&quot; , sans-serif;"><a href="https://www.knowledgefactory.net/p/donate.html" target="_blank"><img border="0" data-original-height="66" data-original-width="259" height="40" src="https://1.bp.blogspot.com/-8lUvUA7TCFo/XX0gOS4ipoI/AAAAAAAAANM/3icmZ9n-e_kvNCPJKDkj5hV_7DeqifIOwCPcBGAYYCw/s200/coffe.png" width="170"></a></span></span></div>
<span style="background-color: white;"><span style="font-family: &quot;trebuchet ms&quot; , sans-serif;">
</span></span></div>
<script src="//uprimp.com/bnr.php?section=General&amp;pub=629848&amp;format=300x250&amp;ga=g" type="text/javascript"></script>
<noscript><a href="https://yllix.com/publishers/629848" target="_blank"><img alt="ylliX - Online Advertising Network" src="//ylx-aff.advertica-cdn.com/pub/300x250.png" style="border:none;margin:0;padding:0;vertical-align:baseline;" /></a></noscript>
</div>
