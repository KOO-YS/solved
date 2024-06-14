
### [실무 역량 과제] API 서버 개발

> ### Problem
>
> https://school.programmers.co.kr/skill_check_assignments/430

---

# Solution

### project.App

```java
package project;
import java.io.IOException;

import project.server.ApiServer;

public class App 
{
    public static void main( String[] args ) throws IOException 
    {
        ApiServer apiServer = new ApiServer();
    }
}
```


### project.server.ApiServer

```java
package project.server;
import com.sun.net.httpserver.HttpServer;
import java.net.InetSocketAddress;
import java.io.File;
import java.io.IOException;
import java.io.OutputStream;

import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;

import com.fasterxml.jackson.databind.ObjectMapper;
import org.json.simple.JSONObject;

public class ApiServer {
    private final int PORT = 5678; 
    private HttpServer httpServer;
    
    private final String MSG_PATH = "/";
    private final String SUM_PATH = "/sum";

    public ApiServer() throws IOException {
        httpServer = HttpServer.create(new InetSocketAddress(PORT), 0);
        httpServer.createContext(MSG_PATH, new GetHandler());
        httpServer.createContext(SUM_PATH, new SumGetHandler());
        httpServer.setExecutor(null);
        httpServer.start();
    }


    class GetHandler implements HttpHandler {

        @Override
        public void handle(HttpExchange exchange) throws IOException {
            String response = "{\"message\":\"server check\"}";

            exchange.getResponseHeaders()
                .add("Content-Type", "application/json");
            exchange.sendResponseHeaders(200, response.getBytes().length);
            OutputStream output = exchange.getResponseBody();
            output.write(response.getBytes());
            output.close();
        }

    }

    class SumGetHandler implements HttpHandler {

        @Override
        public void handle(HttpExchange exchange) throws IOException {
            int postCount = getPostCount();
            String response = "{\"sum\":\""+postCount+"\"}";

            exchange.getResponseHeaders()
                .add("Content-Type", "application/json");
            exchange.sendResponseHeaders(200, response.getBytes().length);
            OutputStream output = exchange.getResponseBody();
            output.write(response.getBytes());
            output.close();    
        }

        int getPostCount() {
            int count = 0;
            
            String filePath = "data/input/user.json";
            ObjectMapper mapper = new ObjectMapper();
            try {
                JSONObject[] jsonList = mapper.readValue(new File(filePath), JSONObject[].class);
                
                for (JSONObject json : jsonList) {
                    count += (int) json.get("post_count");
                }
            } catch (Exception e) {
                // TODO : ERROR LOG
            }
            return count;
        }

    }
    
}

```