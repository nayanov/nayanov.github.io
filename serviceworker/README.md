Test Firebase Cloud Messaging
-----------------------------

You can test usage on page: https://nayanov.github.io/serviceworker/

<img src="ScreenRecord.gif" alt="" align="center">

> Firebase loses the `image` from the notification.
> You can fix the problem by specifying a `image` in `data`.
> And you must see [this](https://github.com/firebase/quickstart-js/issues/71) issue.


Send notification from HTTP client
----------------------------------

```
POST /fcm/send HTTP/1.1
Host: fcm.googleapis.com
Authorization: key=AAAACV7cf7A:APA91bGFsaAtu8Idimw3We2B3YdVmQjGsxb9aN_DFo8OuAb8-qGypwMi5jZRqwC88YNm6NsbeeA0IuTvCQ4vSgqB49n05iKWx0DsNTAtruykqeeFngjakBMFc7rR9I4L2cfy5dFMkZ1N
Content-Type: application/json

{
  "data": {
    "title": "Bubble Nebula",
    "body": "It's found today at 21:00",
    "icon": "https://peter-gribanov.github.io/serviceworker/Bubble-Nebula.jpg",
    "image": "https://peter-gribanov.github.io/serviceworker/Bubble-Nebula_big.jpg",
    "click_action": "https://www.nasa.gov/feature/goddard/2016/hubble-sees-a-star-inflating-a-giant-bubble"
  }
  "to": "YOUR-TOKEN-ID"
}
```

Send notification by cURL
-------------------------

```bash
curl -d '
{
  "data": {
    "title": "Bubble Nebula",
    "body": "It`s found today at 21:00",
    "icon": "https://peter-gribanov.github.io/serviceworker/Bubble-Nebula.jpg",
    "image": "https://peter-gribanov.github.io/serviceworker/Bubble-Nebula_big.jpg",
    "click_action": "https://www.nasa.gov/feature/goddard/2016/hubble-sees-a-star-inflating-a-giant-bubble"
  }
  "to": "YOUR-TOKEN-ID"
}' \
    -H "Content-Type: application/json" \
    -H "Authorization: key=AAAACV7cf7A:APA91bGFsaAtu8Idimw3We2B3YdVmQjGsxb9aN_DFo8OuAb8-qGypwMi5jZRqwC88YNm6NsbeeA0IuTvCQ4vSgqB49n05iKWx0DsNTAtruykqeeFngjakBMFc7rR9I4L2cfy5dFMkZ1N" \
    -X POST "https://fcm.googleapis.com/fcm/send"
```

Warning
-------

This application runs in [GitHub Pages](https://pages.github.com/) at address [/serviceworker/](https://peter-gribanov.github.io/serviceworker/) and this path cannot be changed. Therefore, the [original library](http://www.gstatic.com/firebasejs/3.7.2/firebase.js) is [copied](https://github.com/peter-gribanov/serviceworker/blob/master/firebase.js) to this application and the path to `firebase-messaging-sw.js` has been changed.

If you want to copy this application to your website and run it at the root path, you must [use](https://github.com/peter-gribanov/serviceworker/blob/master/index.html#L95) the [original library](http://www.gstatic.com/firebasejs/3.7.2/firebase.js) and change [path](https://github.com/peter-gribanov/serviceworker/blob/master/app.js#L100) to the serviceworker.
