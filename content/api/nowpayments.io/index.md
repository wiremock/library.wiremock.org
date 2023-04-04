---
slug: "nowpayments-io"
title: "NOWPayments API"
provider: "nowpayments.io"
description: "NOWPayments is a non-custodial cryptocurrency payment processing platform.\
  \ Accept payments in a wide range of cryptos and get them instantly converted into\
  \ a coin of your choice and sent to your wallet. Keeping it simple – no excess.\n\
  \n# Sandbox\n\nBefore production usage, you can test our API using the Sandbox.\
  \ Details can be found [here](https://documenter.getpostman.com/view/7907941/T1LSCRHC)\n\
  \n# Authentication\n\nTo use the NOWPayments API you should do the following:\n\n\
  *   Sign up at [nowpayments.io](https://nowpayments.io)\n*   Specify your outcome\
  \ wallet\n*   Generate an API key\n    \n\n# Standard e-commerce flow for NOWPayments\
  \ API:\n\n1.  API - Check API availability with the [\"GET API status\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#9998079f-dcc8-4e07-9ac7-3d52f0fd733a)\
  \ method. If required, check the list of available payment currencies with the [\"\
  GET available currencies\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#1c268f89-4fe7-471e-81b4-5a3153577b73)\
  \ method.\n2.  UI - Ask a customer to select item/items for purchase to determine\
  \ the total sum;\n3.  UI - Ask a customer to select payment currency\n4.  API -\
  \ Get the minimum payment amount for the selected currency pair (payment currency\
  \ to your Outcome Wallet currency) with the [\"GET Minimum payment amount\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#41b02221-2d58-4fcf-9529-59d3763d6434)\
  \ method;\n5.  API - Get the estimate of the total amount in crypto with [\"GET\
  \ Estimated price\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#7025cacf-7040-4c7b-a83f-f9ff0a22a822)\
  \ and check that it is larger than the minimum payment amount from step 4;\n6. \
  \ API - Call the [\"POST Create payment\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#5e37f3ad-0fa1-4292-af51-5c7f95730486)\
  \ method to create a payment and get the deposit address (in our example, the generated\
  \ BTC wallet address is returned from this method);\n7.  UI - Ask a customer to\
  \ send the payment to the generated deposit address (in our example, user has to\
  \ send BTC coins);\n8.  UI - A customer sends coins, NOWPayments processes and exchanges\
  \ them (if required), and settles the payment to your Outcome Wallet (in our example,\
  \ to your ETH address);\n9.  API - You can get the payment status either via our\
  \ IPN callbacks or manually, using [\"GET Payment Status\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#0b77a8e3-2344-4760-a0bd-247da067db6d)\
  \ and display it to a customer so that they know when their payment has been processed.\n\
  10.  API - you call the list of payments made to your account via the [\"GET List\
  \ of payments\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#c8399c0e-d798-4f01-83ae-ddaa6905c2da)\
  \ method. Additionally, you can see all of this information in your [Account](https://account.nowpayments.io/payments)\
  \ on NOWPayments website.\n    \n\n## Alternative flow\n\n1.  API - Check API availability\
  \ with the [\"GET API status\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#9998079f-dcc8-4e07-9ac7-3d52f0fd733a)\
  \ method. If required, check the list of available payment currencies with the [\"\
  GET available currencies\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#1c268f89-4fe7-471e-81b4-5a3153577b73)\
  \ method.\n2.  UI - Ask a customer to select item/items for purchase to determine\
  \ the total sum;\n3.  UI - Ask a customer to select payment currency\n4.  API -\
  \ Get the minimum payment amount for the selected currency pair (payment currency\
  \ to your Outcome Wallet currency) with the [\"GET Minimum payment amount\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#41b02221-2d58-4fcf-9529-59d3763d6434)\
  \ method;\n5.  API - Get the estimate of the total amount in crypto with [\"GET\
  \ Estimated price\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#7025cacf-7040-4c7b-a83f-f9ff0a22a822)\
  \ and check that it is larger than the minimum payment amount from step 4;\n6. \
  \ API - Call the [\"POST Create Invoice](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#3e3ce25e-f43f-4636-bbd9-11560e46048b)\
  \ method to create an invoice. Set \"success_url\" - parameter so that the user\
  \ will be redirected to your website after successful payment.\n7.  UI - display\
  \ the invoice url or redirect the user to the generated link.\n8.  NOWPayments -\
  \ the customer completes the payment and is redirected back to your website (only\
  \ if \"success_url\" parameter is configured correctly!).\n9.  API - You can get\
  \ the payment status either via our IPN callbacks or manually, using [\"GET Payment\
  \ Status\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#0b77a8e3-2344-4760-a0bd-247da067db6d)\
  \ and display it to a customer so that they know when their payment has been processed.\n\
  10.  API - you call the list of payments made to your account via the [\"GET List\
  \ of payments\"](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#c8399c0e-d798-4f01-83ae-ddaa6905c2da)\
  \ method. Additionally, you can see all of this information in your [Account](https://account.nowpayments.io/invoices)\
  \ on NOWPayments website.\n    \n\n# API Documentation\n\n## Instant Payments Notifications\n\
  \nIPN (Instant payment notifications, or callbacks) are used to notify you when\
  \ transaction status is changed.  \nTo use them, you should complete the following\
  \ steps:\n\n1.  Generate and save the IPN Secret key in Store Settings tab at the\
  \ Dashboard.\n2.  Insert your URL address where you want to get callbacks in create_payment\
  \ request. The parameter name is ipn_callback_url. You will receive payment updates\
  \ (statuses) to this URL address.\n3.  You will receive all the parameters at the\
  \ URL address you specified in (2) by POST request.  \n    The POST request will\
  \ contain the *x-nowpayments-sig* parameter in the header.  \n    The body of the\
  \ request is similiar to a [get payment status](https://documenter.getpostman.com/view/7907941/S1a32n38?version=latest#0b77a8e3-2344-4760-a0bd-247da067db6d)\
  \ response body.  \n    Example:  \n    {\"payment_id\":5077125051,\"payment_status\"\
  :\"waiting\",\"pay_address\":\"0xd1cDE08A07cD25adEbEd35c3867a59228C09B606\",\"price_amount\"\
  :170,\"price_currency\":\"usd\",\"pay_amount\":155.38559757,\"actually_paid\":0,\"\
  pay_currency\":\"mana\",\"order_id\":\"2\",\"order_description\":\"Apple Macbook\
  \ Pro 2019 x 1\",\"purchase_id\":\"6084744717\",\"created_at\":\"2021-04-12T14:22:54.942Z\"\
  ,\"updated_at\":\"2021-04-12T14:23:06.244Z\",\"outcome_amount\":1131.7812095,\"\
  outcome_currency\":\"trx\"}\n4.  Sort all the parameters from the POST request in\
  \ alphabetical order.\n5.  Convert them to string using  \n    [JSON.stringify](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)\
  \ (params, Object.keys(params).sort()) or the same function.\n6.  Sign a string\
  \ with an IPN-secret key with HMAC and sha-512 key\n7.  Compare the signed string\
  \ from the previous step with the x-nowpayments-sig , which is stored in the header\
  \ of the callback request.  \n    If these strings are similar it is a success.\
  \  \n    Otherwise, contact us on [support@nowpayments.io](mailto:support@nowpayments.io)\
  \ to solve the problem.\n    \n\nExample of creating a signed string at Node.JS\n\
  \n```\nconst hmac = crypto.createHmac('sha512', notificationsKey);\nhmac.update(JSON.stringify(params,\
  \ Object.keys(params).sort()));\nconst signature = hmac.digest('hex');\n\n```\n\n\
  Example of comparing signed strings in PHP\n\n```\nfunction check_ipn_request_is_valid()\n\
  \    {\n        $error_msg = \"Unknown error\";\n        $auth_ok = false;\n   \
  \     $request_data = null;\n        if (isset($_SERVER['HTTP_X_NOWPAYMENTS_SIG'])\
  \ && !empty($_SERVER['HTTP_X_NOWPAYMENTS_SIG'])) {\n            $recived_hmac =\
  \ $_SERVER['HTTP_X_NOWPAYMENTS_SIG'];\n            $request_json = file_get_contents('php://input');\n\
  \            $request_data = json_decode($request_json, true);\n            ksort($request_data);\n\
  \            $sorted_request_json = json_encode($request_data, JSON_UNESCAPED_SLASHES);\n\
  \            if ($request_json !== false && !empty($request_json)) {\n         \
  \       $hmac = hash_hmac(\"sha512\", $sorted_request_json, trim($this->ipn_secret));\n\
  \                if ($hmac == $recived_hmac) {\n                    $auth_ok = true;\n\
  \                } else {\n                    $error_msg = 'HMAC signature does\
  \ not match';\n                }\n            } else {\n                $error_msg\
  \ = 'Error reading POST data';\n            }\n        } else {\n            $error_msg\
  \ = 'No HMAC signature sent.';\n        }\n    }\n\n```\n\n## Recurrent payment\
  \ notifications\n\nIf an error is detected, the payment is flagged and will receive\
  \ additional recurrent notifications (number of recurrent notifications can be changed\
  \ in your Store Settings-> Instant Payment Notifications).\n\nIf an error is received\
  \ again during processing of the payment, recurrent notifications will be initiated\
  \ again.\n\nExample: \"Timeout\" is set to 1 minute and \"Number of recurrent notifications\"\
  \ is set to 3.\n\nOnce an error is detected, you will receive 3 notifications at\
  \ 1 minute intervals.\n\n## Several payments for one order\n\nIf you want to create\
  \ several payments for one Order you should do the following:\n\n*   Create a payment\
  \ for the full order amount.\n*   Save \"purchase_id\" which will be in \"create_payment\"\
  \ response\n*   Create next payment or payments with this \"purchase_id\" in \"\
  create_payment\" request.\n*   **Only works for partially_paid payments**\n    \n\
  \nIt may be useful if you want to give your customers opportunity to pay a full\
  \ order with several payments, for example, one part in BTC and one part in ETH.\
  \ Also, if your customer accidentally paid you only part of a full amount, you can\
  \ automatically ask them to make another payment.\n\n## Packages\n\nPlease find\
  \ our out-of-the box packages for easy integration below:\n\n[JavaScript package](https://www.npmjs.com/package/@nowpaymentsio/nowpayments-api-js)\n\
  \n\\[PHP package\\]  \n([https://packagist.org/packages/nowpayments/nowpayments-api-php](https://packagist.org/packages/nowpayments/nowpayments-api-php))\n\
  \nMore coming soon!\n\n## Payments"
logo: "nowpayments.io-logo.svg"
logoMediaType: "image/svg+xml"
tags:
- "financial"
stubs: "nowpayments.io-stubs.json"
swagger: "nowpayments.io-swagger.json"
---