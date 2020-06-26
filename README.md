# deno-lambda-project-001





### myhandler.js

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
