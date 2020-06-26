# deno-lambda-project-001





### myhandler.js - 1st version 

<pre><code>
import {
  APIGatewayProxyEvent, // this can be any input event ex. S3Event, DynamoDBEvent
  APIGatewayProxyResult, // this can be any result type ex. S3Result, DynamoDBResult 
  Context
} from "https://deno.land/x/lambda/mod.ts";

export async function handler(
  event: APIGatewayProxyEvent,
  context: Context,
): Promise<APIGatewayProxyResult> {
  return {
    statusCode: 200,
    headers: { "content-type": "text/html;charset=utf8" },
    body: `Welcome to deno ${Deno.version.deno} 🦕`,
  };
}
</code></pre>

### myhandler.js - 2nd version 

<pre><code>
import {
  APIGatewayProxyEvent, // this can be any input event ex. S3Event, DynamoDBEvent
  APIGatewayProxyResult, // this can be any result type ex. S3Result, DynamoDBResult 
  Context
} from "https://deno.land/x/lambda/mod.ts";

export async function handler(
  event: APIGatewayProxyEvent,
  context: Context,
): Promise<APIGatewayProxyResult> {
  
  let result = 'google is down';
  
  // use HTTPS to interact with backend system 
  const res = await fetch('https://www.google.com/');
  console.log(res.status);
  if (res.status == 200) {
    result = 'google is running';
  }
  
  return {
    statusCode: 200,
    headers: { "content-type": "text/html;charset=utf8" },
    body: result,
  };
}

</code></pre>






