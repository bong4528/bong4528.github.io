## Byte Code Instrumentation in Java

출처: https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=rbtjqtjql&logNo=220993460343

BCI (Byte Code Instrumentation)?

Java의 **Byte Code 에 직접 수정**을 가해서, **소스 파일의 수정 없이 원하는 기능을 부여**하는 기법이다.


이러한 특징때문에 대부분의 Java 프로파일러나 모니터링 툴들이 BCI 기능을 사용하고 있다.

BCI는 앞서 작성한 AOP에서 말하는 Loading Time Weaving의 핵심 기술이다.

아래 소스 코드는 java.lang.Exception 클래스를 ASM Library를 이용해 읽고(Read), 변형없이 쓰는(Write) 예제이다.

```
package flowlite.exception2;
import java.io.FileOutputStream;
import org.objectweb.asm.*;
import org.objectweb.asm.commons.*;

public class ExceptionTransformaer implements Opcodes {
     //Convert class
     public void transform(String newClassName) throws Exception{
          System.out.println("Starting transformation of java.lang.Exception...");
          
          //Reader
          ClassReader reader = new ClassReader("java.lang.Exception");
          //Writer
          ClassWriter writer = new ClassWriter(ClassWriter.COMPUTE_MAXS);
          //Class Adapter
          ClassAdapter adapter = new ExceptionClassAdapter(writer);

          reader.accept(adapter, ClassReader.SKIP_FRAMES);
     
          byte[] b = writer.toByteArray();
          FileOutputStream fos = new FileOutputStream(newClassName + ".class");
          fos.write(b);
          fos.flush();
     }

     public static void main(String[] args){
          try{
               String newClassName = "Exception";
               if(args.length >= 1) newClassName = args[0];
               ExceptionTransformer fit = new ExceptionTransformaer();
               fit.transform(newClassName);
          }catch(Exception ex){
               ex.printStackTrace();
          }
     }

     class ExceptionClassAdapter extends Classadapter implements Opcodes
     {
          public ExceptionClassAdapter(ClassVisitor visitor){
               super(visitor);
          }
     }
}
```
ClassReader 객체를 이용해 원래 클래스의 바이트 코드를 읽어들인다.
ClassAdapter 객체를 이용해 바이트 코드를 변경한다.
ClassWriter 객체를 이용해서 변경된 바이트 코드를 얻는다.


자, 우리는 원래의 Exception 클래스를 변경(하진 않았지만)하여 새로운 Exception 클래스를 생성하고 파일을 확인하였다.

**문제는 어떻게 하면 JVM의 rt.jar에서 제공하는 java.lang.Exception 클래스 파일이 아닌, 내가 생성한 Exception 클래스 파일을 쓰게 하느냐이다.**
 
rt.jar파일을 직접 변경시킬순 없고 (매우 위험하고 법적인 문제가 될 수 있음!) **답은 -Xbootclasspath 옵션**을 이용하는 것이다.

명령행에 java -X를 입력해보면 아래과 같은 결과를 얻을 수 있다.
