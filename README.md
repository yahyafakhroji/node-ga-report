Google Analytics Reporting [![Build Status](https://drone.io/github.com/Turistforeningen/node-ga-report/status.png)](https://drone.io/github.com/Turistforeningen/node-ga-report/latest)
==========================

[![Join the chat at https://gitter.im/Turistforeningen/node-ga-report](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/Turistforeningen/node-ga-report?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

[![NPM](https://nodei.co/npm/ga-report.png?downloads=true)](https://www.npmjs.org/package/ga-report)

NodeJS wrapper for Google Analytics Core Reporting API

# Install

```bash
npm install ga-report
```

# API

## Instanciate

```javascript
var Report = require('ga-report');

var report = new Report({'username':'user@gmail.com', 'password':'mypassword'});
report.once('ready', function() {
  // ready to report
});
```

## Get Accounts

[Account object documentation](https://developers.google.com/analytics/devguides/config/mgmt/v3/mgmtReference/management/accounts).

```javascript
report.getAccounts(function(err, accounts) {
  console.error(err);
  for (var i = 0; i < accounts.length; i++) {
    console.log(accounts[i]);
  }
});
```

## Get Web Properties

[Web Property object documentation](https://developers.google.com/analytics/devguides/config/mgmt/v3/mgmtReference/management/webproperties).

```javascript
report.getWebproperties(accountId, function(err, webproperties) {
  console.error(err);
  for (var i = 0; i < webproperties.length; i++) {
    console.oog(webproperties[i]);
  }
});
```

## Get Views (Profiles)

[Profile object documentation](https://developers.google.com/analytics/devguides/config/mgmt/v3/mgmtReference/management/profiles).

```javascript
report.getProfiles(accountId, webpropertyId, function(err, profile) {
  console.error(err);
  for (var i = 0; i < profiles.length; i++) {
    console.oog(profiles[i]);
  }
});
```

## Get Report

```javascript
var options = {
  'ids': 'ga:123456-UA',
  'start-date': '2013-10-01',
  'end-date': '2013-10-31',
  'metrics': 'ga:visits,ga:bounces'
};
report.get(options, function(err, data) {
  if (err) console.error(err);
  console.dir(data);
});
```

# Other Documentation

 * [GA Query Explorer](http://ga-dev-tools.appspot.com/explorer/)
 * [GA Core Reporting API](https://developers.google.com/analytics/devguides/reporting/core/v3/reference)
 * [GA Management API](https://developers.google.com/analytics/devguides/config/mgmt/v3/mgmtReference/)


## The MIT License (MIT)

Copyright (c) 2014 Turistforeningen

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

