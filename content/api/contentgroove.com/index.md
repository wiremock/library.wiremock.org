---
slug: "contentgroove-com"
title: "ContentGroove API"
provider: "contentgroove.com"
description: "# Overview\n\nThe ContentGroove Developer API enables you to add the\
  \ power of ContentGroove's video AI to your own applications and workflows.\n\n\
  Webhooks are a way for ContentGroove to send video information\nto your application,\
  \ to update your system and/or trigger other business processes.\n\nYou can use\
  \ Webhooks and the Developer API separately or together.\n\n# Getting Started with\
  \ Webhooks\n\n- Sign up for an account at [app.contentgroove.com](https://app.contentgroove.com)\n\
  - Read \"Using Webhooks\" on the [API Reference page](https://developers.contentgroove.com/api_reference)\n\
  - Visit the [Webhooks page](https://app.contentgroove.com/webhook_subscriptions)\
  \ and create a new webhook\n\n# Using Webhooks\n\nWebhooks, also known as callbacks,\
  \ are a way for ContentGroove to notify your application as soon as possible after\
  \ an event has occurred in ContentGroove.\nFor example after a media completes processing,\
  \ ContentGroove can use a webhook to notify your application with information about\
  \ the video: Suggested clips, transcription, and so on.\nYou can use the information\
  \ sent to update your system and/or use the\nwebhook to trigger other business processes.\n\
  \nThe webhook request is sent as an HTTP POST containing a payload of JSON-formatted\
  \ data.\nFor the details of the payload format see the \"CALLBACKS\" sections below.\n\
  \nWhen your application receives the webhook request, it must respond with\na 200\
  \ HTTP status code (success).\nIf a 200 HTTP status code is not returned,\nContentGroove\
  \ will assume that the webhook was not delivered and\nwill retry a limited number\
  \ of times, using an exponential backoff algorithm.\n\nContentGroove makes a best\
  \ effort to attempt to send the webhook at\nleast once.\nApplications receiving\
  \ webhooks must tolerate the\npossibility of a single webhook payload being sent\
  \ more than once\n(idempotent behavior).\nApplications receiving webhooks should\
  \ tolerate the possibility that\na webhook could not be delivered\n(for example\
  \ your application was down when delivery was attempted).\n\n# Getting Started with\
  \ the Developer API\n\n- Sign up for an account at [app.contentgroove.com](https://app.contentgroove.com)\n\
  - Visit the [API Keys page](https://app.contentgroove.com/api_keys)\n  - Create\
  \ a new API Key then copy and save the value.\n    > ⚠️ **IMPORTANT**: This API\
  \ Key is intended only for use on the server side. Be sure never to use a server-side\
  \ API Key in client-side (web, mobile, or otherwise) code. ⚠️\n- View all available\
  \ endpoints, and try the API, on our [API Reference page](https://developers.contentgroove.com/api_reference)\n\
  \n# Using the Developer API\n\n- Create a new media (video or audio) in ContentGroove\n\
  \  - If the video or audio is available from a URL, you can create a media by providing\
  \ the `source_url` parameter. ContentGroove will fetch the video or audio from the\
  \ URL if possible.\n  - Or, you can create a media from a video or audio file which\
  \ you upload directly to ContentGroove (see File Uploading section below).\n- After\
  \ the new media is created, at first it will be in a \"processing\" state.\n  Depending\
  \ on the size and duration of the video or audio file, it will take some time for\
  \ processing to complete.\n  - You can use ContentGroove Webhooks to be notified\
  \ immediately when processing has completed. (Details coming soon.)\n  - You can\
  \ also use the API to read the state of the media, to determine if the media has\
  \ completed processing yet.\n- After the media has completed processing, you can\
  \ access all of these details about the media:\n  - The media name and description\n\
  \  - The transcription of spoken words\n  - Topics and keywords which were discussed\
  \ in the transcription\n  - Suggested video clips are automatically created\n- In\
  \ addition to the automatically created video clips, you can create more video clips\
  \ from the media\n\n# Response Codes\n\nThe following is a comprehensive list of\
  \ the status codes you may receive while using the ContentGroove API:\n\n- 200 \"\
  Ok\"\n  - The request was valid\n- 400 \"Bad Request\n  - This is returned when\
  \ there was a problem parsing the JSON body of your request if you supplied the\
  \ 'Content-Type': 'application/json' header, or if your request is missing the 'Content-Type'\
  \ header altogether\n- 401 \"Unauthorized\"\n  - This is returned when you are attempting\
  \ to perform an action on a resource that you are not authorized to do\n- 402 \"\
  Payment Required\"\n  - This is returned when you are attempting to perform an action\
  \ that would push your account above a usage limit. You can view your usage at:\
  \ https://app.contentgroove.com/quota_usage\n- 404 \"Not Found\"\n  - This is returned\
  \ when the resource you are trying to view does not exist\n- 429 \"Too Many Requests\"\
  \n  - This is returned when you have performed too many requests within a given\
  \ period of time\n- 500 \"Internal Server Error\"\n  - This is returned when your\
  \ request was valid but there was a problem on our end\n\n# File Uploading\n\n-\
  \ Step 1: Make a GET request to the direct uploads URL endpoint (/api/v1/direct_uploads)\
  \ to receive an upload URL to upload the file to and an upload id.\n- Step 2: Make\
  \ a PUT request with the file as the body to the upload URL received in step 1.\
  \ The response will have a 200 status with no body if the upload is successful.\n\
  \  ```\n  curl -T /path/to/file upload_url\n  ```\n- Step 3: After uploading the\
  \ file to the upload URL, make a POST request to the create medias endpoint (/api/v1/medias),\
  \ with the upload id and optionally a name and description for the new media.\n\
  \  > At this time, file uploads are limited to 5gb per file.\n\n# Allowed media\
  \ types\n\nVideo:\n\n- Supported: Most common video formats and codecs are supported.\n\
  - Recommended: mp4\n\nAudio:\n\n- Supported: aac, mp3, flac, ogg, wav, and wma\n\
  - Recommended: aac\n\n# Authentication\n\nYou can use the API Key to authenticate\
  \ your API requests using any of these methods. (Replace abc123 with your actual\
  \ API Key.)\n\n- Request header `Authorization: Bearer abc123`\n- Request header\
  \ `X-API-KEY: abc123`\n- Query parameter `api_key=abc123`\n  > ⚠️ **IMPORTANT**:\
  \ This API Key is intended only for use on the server side. Be sure never to use\
  \ a server-side API Key in client-side (web, mobile, or otherwise) code. ⚠️\n\n\
  # Link to openapi.json spec\n\n- https://api.contentgroove.com/api-docs/v1/openapi.json\n"
logo: "contentgroove.com-logo.png"
logoMediaType: "image/png"
tags: []
stubs: "contentgroove.com-stubs.json"
swagger: "contentgroove.com-swagger.json"
---
