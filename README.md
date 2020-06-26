# deno-lambda-project-001

### step01: build custom deno runtime - using Lambda Layer 
-> show no built-in deno runtime
-> introduce SAR as a thing to use existing Lambda layer 
-> create it 
-> check cloudformation stack 
### step02: create a dummy lambda
### step02-01: add Lambda layer 
### step02-02: complete handler code (1st version) 
-> check handler setting 
### step03: test it 
### step04: modify handler code (2nd version)
-> kind of show a feel how to use deno lambda in a real world 
### step05: test it 



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






