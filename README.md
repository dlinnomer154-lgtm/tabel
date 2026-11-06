[index.html](https://github.com/user-attachments/files/34484779/index.html)
<!DOCTYPE html>
<html lang="ru"><head><script data-bard-client-injected="true">(function(firebaseConfig, initialAuthToken, appId) {
        window.__firebase_config = firebaseConfig;
        window.__initial_auth_token = initialAuthToken;
        window.__app_id = appId;
            })("\n{\n  \"apiKey\": \"AIzaSyCqyCcs2R2e7AegGjvFAwG98wlamtbHvZY\",\n  \"authDomain\": \"bard-frontend.firebaseapp.com\",\n  \"projectId\": \"bard-frontend\",\n  \"storageBucket\": \"bard-frontend.firebasestorage.app\",\n  \"messagingSenderId\": \"175205271074\",\n  \"appId\": \"1:175205271074:web:2b7bd4d34d33bf38e6ec7b\"\n}\n","eyJhbGciOiJSUzI1NiIsImtpZCI6IjExNjRiNzdiNDMzZDdhMDAyMWI4NjE4YjhjYTU3ZTMyZGI5MWUxMTMiLCJ0eXAiOiJKV1QifQ.eyJzdWIiOiJmaXJlYmFzZS1hZG1pbnNkay1mYnN2Y0BiYXJkLWZyb250ZW5kLmlhbS5nc2VydmljZWFjY291bnQuY29tIiwiYXVkIjoiaHR0cHM6Ly9pZGVudGl0eXRvb2xraXQuZ29vZ2xlYXBpcy5jb20vZ29vZ2xlLmlkZW50aXR5LmlkZW50aXR5dG9vbGtpdC52MS5JZGVudGl0eVRvb2xraXQiLCJ1aWQiOiIwMDkxNTk0ODgzNzc1NzQ0ODMzMCIsImlzcyI6ImZpcmViYXNlLWFkbWluc2RrLWZic3ZjQGJhcmQtZnJvbnRlbmQuaWFtLmdzZXJ2aWNlYWNjb3VudC5jb20iLCJjbGFpbXMiOnsiYXBwSWQiOiJjXzlkODU2NzFkZmNlMDA0MDNfaW5kZXguaHRtbC0xMDUifSwiZXhwIjoxNzkzOTc0NzA1LCJpYXQiOjE3OTM5NzExMDUsImFsZyI6IlJTMjU2In0.HTLWOlNXBPdAWE906GAldnoBiWw7Z1jgqoHWmvbl8kSyxzjftnRvorvL-s4du7bALJYSKwS1KNSnu4aGRHflnAwfGa7p5_qe0k4SMToRO63Rmmyk68xKChH6Q7m0elJKs2D3SKaeTpI6w1RPH3gIl7b9y-60pIy3JMXAZp4r59sSZQvEYI6FdZ3TK6iq6HlLlrJt_itlQB3Sw-53A86GcHd3Vjzkq7fT9MsQpjN2IigW7_NGr0he7NYKQ7Eyylim3LQlYPypiKmcm3UPe5Gd83APKiE7kJDqO4tXw7Spex_SpEP1JlGtYz6Mr5ATLKhV0N5EWVa-6flTQkxNx-yDng","c_9d85671dfce00403_index.html-105")</script><script data-bard-client-injected="true">
  document.addEventListener('input', (event) => {
    if (event.target && (event.target.isContentEditable || event.target.hasAttribute('contenteditable'))) {
      const clonedDoc = document.cloneNode(true);
      const injectedScripts = clonedDoc.querySelectorAll('[data-bard-client-injected="true"]');
      injectedScripts.forEach(el => el.remove());
      window.parent.postMessage({
        type: 'inlineEdit',
        html: '<!DOCTYPE html>\n' + clonedDoc.documentElement.outerHTML
      }, '*');
    }
  });
</script><script data-bard-client-injected="true">(function(){'use strict';window.addEventListener("message",a=>{a.data&&a.data.type==="SUPPLEMENTAL_DATA_UPDATE"&&window.dispatchEvent(new CustomEvent("supplementaldataupdate",{detail:a.data.data}))});}).call(this);
</script><script data-bard-client-injected="true">(function() {
  const SCROLL_KEYS = new Set([
    'ArrowUp', 'ArrowDown', 'ArrowLeft', 'ArrowRight',
    ' ', 'Spacebar', 'PageUp', 'PageDown', 'Home', 'End',
  ]);
  const HORIZONTAL_KEYS = new Set(['ArrowLeft', 'ArrowRight']);

  function isTextEntryTarget(target) {
    if (!target) return false;
    const tagName = target.tagName;
    return tagName === 'INPUT' || tagName === 'TEXTAREA' ||
        tagName === 'SELECT' || target.isContentEditable === true;
  }

  // An element absorbs the key only if it both overflows on the axis being
  // scrolled and is configured to scroll on that axis. The cheap dimension
  // test runs first because getComputedStyle forces a style recalc, and this
  // runs on every keypress. Each axis is read from its own longhand: the
  // 'overflow' shorthand serializes as two values when the axes differ, which
  // is the common 'overflow-x: hidden; overflow-y: auto' pane.
  function canScroll(node, horizontal) {
    const overflows = horizontal ? node.scrollWidth > node.clientWidth
                                 : node.scrollHeight > node.clientHeight;
    if (!overflows) return false;
    const style = window.getComputedStyle(node);
    const overflow = horizontal ? style.overflowX : style.overflowY;
    return overflow === 'auto' || overflow === 'scroll';
  }

  // Walks up from the event target so nested scrollers keep their behavior.
  // <body> is included because pages that pin the root height make it the
  // scroll container.
  function hasScrollableAncestor(target, horizontal) {
    let node = target;
    while (node && node !== document.documentElement) {
      if (canScroll(node, horizontal)) return true;
      node = node.parentElement;
    }
    return false;
  }

  function rootCanScroll(horizontal) {
    const scroller = document.scrollingElement || document.documentElement;
    if (!scroller) return false;
    // Tolerate a pixel of rounding so subpixel layouts do not look scrollable.
    return horizontal ? scroller.scrollWidth > window.innerWidth + 1
                      : scroller.scrollHeight > window.innerHeight + 1;
  }

  window.addEventListener('keydown', function(event) {
    if (!SCROLL_KEYS.has(event.key)) return;
    if (event.defaultPrevented) return;
    // Alt and Meta turn arrows into browser history navigation, and Ctrl is
    // reserved for shortcuts, so none of them are scroll intent.
    if (event.altKey || event.metaKey || event.ctrlKey) return;

    const target = event.target;
    if (isTextEntryTarget(target)) return;

    // Anything that can still absorb the scroll gets to keep it.
    const horizontal = HORIZONTAL_KEYS.has(event.key);
    if (rootCanScroll(horizontal)) return;
    if (hasScrollableAncestor(target, horizontal)) return;

    event.preventDefault();
  }, {capture: true, passive: false});
})();</script><script data-bard-client-injected="true">(function() {
  // Ensure this script is executed only once
  if (window.firebaseAuthBridgeScriptLoaded) {
    return;
  }
  window.firebaseAuthBridgeScriptLoaded = true;

  let nextTokenPromiseId = 0;

  // Stores { resolve, reject } for ongoing token requests
  const pendingTokenPromises = {};

  // Listen for messages from the Host Application
  window.addEventListener('message', function(event) {

    const messageData = event.data;

  if (messageData && messageData.type === 'RESOLVE_NEW_FIREBASE_TOKEN') {
      const { success, token, error, promiseId } = messageData ?? {};
      if (pendingTokenPromises[promiseId]) {
        if (success) {
          pendingTokenPromises[promiseId].resolve(token);
        } else {
          pendingTokenPromises[promiseId].reject(new Error(error || 'Token refresh failed from host.'));
        }
        delete pendingTokenPromises[promiseId];
      }
    }
  });

  // Expose a function for the Generated App to request a new Firebase token
  window.requestNewFirebaseToken = function() {
    const currentPromiseId = nextTokenPromiseId++;
    const promise = new Promise((resolve, reject) => {
      pendingTokenPromises[currentPromiseId] = { resolve, reject };
    });
    if (window.parent && window.parent !== window) {
      window.parent.postMessage({
        type: 'REQUEST_NEW_FIREBASE_TOKEN',
        promiseId: currentPromiseId
      }, '*');
    } else {
      pendingTokenPromises[currentPromiseId].reject(new Error('No parent window to request token from.'));
      delete pendingTokenPromises[currentPromiseId];
    }
    return promise;
  };
})();</script><script data-bard-client-injected="true">
let realOriginalGetUserMedia = null;
if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia) {
  realOriginalGetUserMedia = navigator.mediaDevices.getUserMedia.bind(navigator.mediaDevices);
}

(function() {
  if (navigator.mediaDevices && navigator.mediaDevices.__proto__) {
    try {
      Object.defineProperty(navigator.mediaDevices.__proto__, 'getUserMedia', {
        get: function() {
          return undefined; // Or throw an error
        },
        configurable: false
      });
    } catch (error) {
      console.error("Error defining prototype getter:", error);
    }
  }
})();

(function() {
  const pendingMediaResolvers = {};
  let nextMediaPromiseId = 0;

  function requestMediaPermissions(constraints) {
    const mediaPromiseId = nextMediaPromiseId++;
    const promise = new Promise((resolve, reject) => {
      pendingMediaResolvers[mediaPromiseId] = (granted) => {
        delete pendingMediaResolvers[mediaPromiseId];
        resolve(granted);
      };
    });

    window.parent.postMessage({
      type: 'requestMediaPermission',
      constraints: constraints,
      promiseId: mediaPromiseId,
    }, '*');

    return promise;
  }

  let originalGetUserMedia = realOriginalGetUserMedia;

  function interceptGetUserMedia() {
    if (navigator.mediaDevices) {
      Object.defineProperty(navigator.mediaDevices, 'getUserMedia', {
        value: function(constraints) {
          return requestMediaPermissions(constraints).then((granted) => {
            if (granted) {
              if (originalGetUserMedia) {
                return originalGetUserMedia(constraints);
              } else {
                throw new Error("Original getUserMedia not available.");
              }
            } else {
              throw new DOMException('Permission denied', 'NotAllowedError');
            }
          });
        },
        writable: false,
        configurable: false
      });
    }
  }

  interceptGetUserMedia();

  const observer = new MutationObserver(function(mutationsList, observer) {
    for (const mutation of mutationsList) {
      if (mutation.type === 'reconfigured' && mutation.name === 'getUserMedia' && mutation.object === navigator.mediaDevices) {
        interceptGetUserMedia();
      } else if (mutation.type === 'attributes' && mutation.attributeName === 'getUserMedia' && mutation.target === navigator.mediaDevices) {
        interceptGetUserMedia();
      } else if (mutation.type === 'childList' && mutation.addedNodes) {
        mutation.addedNodes.forEach(node => {
          if (node === navigator.mediaDevices) {
            interceptGetUserMedia();
          }
        });
      }
    }
  });

  function interceptSpeechRecognition() {
    if (!window.SpeechRecognition && !window.webkitSpeechRecognition) {
      return;
    }

    const OriginalSpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;

    const SpeechRecognitionWrapper = function(...args) {
      const recognizer = new OriginalSpeechRecognition(...args);
      const originalStart = recognizer.start.bind(recognizer);

      recognizer.start = function() {
        requestMediaPermissions({ audio: true }).then(granted => {
          if (granted) {
            originalStart();
          } else {
            const errorEvent = new SpeechRecognitionErrorEvent('error');
            errorEvent.error = 'not-allowed'; // This is the standard error for permission denial.
            recognizer.dispatchEvent(errorEvent);
          }
        });
      };

      return recognizer;
    };

    SpeechRecognitionWrapper.prototype = OriginalSpeechRecognition.prototype;
    SpeechRecognitionWrapper.prototype.constructor = SpeechRecognitionWrapper;

    if (window.SpeechRecognition) {
      window.SpeechRecognition = SpeechRecognitionWrapper;
    }
    if (window.webkitSpeechRecognition) {
      window.webkitSpeechRecognition = SpeechRecognitionWrapper;
    }
  }

  interceptSpeechRecognition();

  window.addEventListener('message', function(event) {
    if (event.data) {
      if (event.data.type === 'resolveMediaPermission') {
        const { promiseId, granted } = event.data;
        if (pendingMediaResolvers[promiseId]) {
          pendingMediaResolvers[promiseId](granted);
        }
      }
    }
  });

})();</script><script ws-interception-config="{&quot;parentOrigin&quot;:&quot;https://gemini.google.com&quot;,&quot;proxiedDomains&quot;:[]}" data-bard-client-injected="true">(function(){'use strict';var u=typeof Object.defineProperties=="function"?Object.defineProperty:function(b,d,e){if(b==Array.prototype||b==Object.prototype)return b;b[d]=e.value;return b};function v(b){b=["object"==typeof globalThis&&globalThis,b,"object"==typeof window&&window,"object"==typeof self&&self,"object"==typeof global&&global];for(var d=0;d<b.length;++d){var e=b[d];if(e&&e.Math==Math)return e}throw Error("Cannot find global object");}var w=v(this);
function y(b,d){if(d)a:{var e=w;b=b.split(".");for(var h=0;h<b.length-1;h++){var k=b[h];if(!(k in e))break a;e=e[k]}b=b[b.length-1];h=e[b];d=d(h);d!=h&&d!=null&&u(e,b,{configurable:!0,writable:!0,value:d})}}function z(b){function d(h){return b.next(h)}function e(h){return b.throw(h)}return new Promise(function(h,k){function m(n){n.done?h(n.value):Promise.resolve(n.value).then(d,e).then(m,k)}m(b.next())})}y("globalThis",function(b){return b||w});/*

 Copyright The Closure Library Authors.
 SPDX-License-Identifier: Apache-2.0
*/
function A(b,d){function e(){}e.prototype=d.prototype;b.j=d.prototype;b.prototype=new e;b.prototype.constructor=b;b.h=function(h,k,m){for(var n=Array(arguments.length-2),p=2;p<arguments.length;p++)n[p-2]=arguments[p];return d.prototype[k].apply(h,n)}};function B(b,d,e="*"){function h(a){if(typeof a==="string")return F.encode(a).buffer;if(a instanceof ArrayBuffer)return a.slice(0);if(ArrayBuffer.isView(a))return a.buffer.slice(a.byteOffset,a.byteOffset+a.byteLength);throw Error("Invalid data type");}function k(a){a=h(a);var f={type:"send",data:new Uint8Array(a)},g;(g=r)==null||g.postMessage(f,[a])}function m(){if(!r)throw Error("Data port not captured yet.");r.onmessage=a=>{if(a.data.type==="message"){a=new MessageEvent("message",{data:G.decode(a.data.data)});
let f;(f=c.onmessage)==null||f.call(c,a);c.dispatchEvent(a)}}}function n(){if(!t)throw Error("Control port not captured yet.");t.onmessage=a=>{switch(a.data.type){case "open":l=1;var f=new Event("open"),g;(g=c.onopen)==null||g.call(c,f);c.dispatchEvent(f);q.forEach(H=>{k(H)});q=[];break;case "close":g=a.data;l=3;g=new CloseEvent("close",{code:g.code,reason:g.reason,wasClean:g.wasClean});(f=c.onclose)==null||f.call(c,g);c.dispatchEvent(g);break;case "error":l=3;f=new Event("error");let x;(x=c.onerror)==
null||x.call(c,f);c.dispatchEvent(f)}}}function p(a){return z(function*(){var f=new MessageChannel;t=f.port1;var g=new MessageChannel;r=g.port1;n();m();window.parent.postMessage({type:"websocket_open",portOrdering:["control","data"],url:b,protocols:a||[],connectionId:I},e,[f.port2,g.port2])}())}var c=Reflect.construct(EventTarget,[],new.target);c.CONNECTING=0;c.OPEN=1;c.CLOSING=2;c.CLOSED=3;c.url=b;c.binaryType="arraybuffer";c.protocol="";c.i="";var l=0,t=null,r=null,q=[],F=new TextEncoder,G=new TextDecoder;
c.onopen=null;c.onmessage=null;c.onclose=null;c.onerror=null;Object.defineProperty(c,"readyState",{get:()=>l,enumerable:!0,configurable:!0});Object.defineProperty(c,"bufferedAmount",{get:()=>{var a=0;q.forEach(f=>{a+=typeof f==="string"?f.length:f.byteLength});return a},enumerable:!0,configurable:!0});var I=function(){var a;return((a=globalThis.crypto)==null?0:a.randomUUID)?globalThis.crypto.randomUUID():"xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx".replace(/[xy]/g,f=>{var g=Math.random()*16|0;return(f===
"x"?g:g&3|8).toString(16)})}();c.send=a=>{if(l===1)a instanceof Blob?a.arrayBuffer().then(f=>{k(f)}):k(a);else if(l===0)if(typeof a==="string")q.push(a);else if(a instanceof ArrayBuffer||ArrayBuffer.isView(a))q.push(h(a));else throw Error("Sending Blob is not supported before the connection is open.");else console.debug("WebSocket send called in CLOSING or CLOSED state; ignored.")};c.close=(a=1E3,f="")=>{if(l!==2&&l!==3){l=2;a={type:"close",code:a,reason:f,wasClean:a===1E3};var g;(g=t)==null||g.postMessage(a)}};
Promise.resolve().then(()=>p(d));return c}A(B,EventTarget);var C=document.currentScript,D=C==null?void 0:C.getAttribute("ws-interception-config");if(!D)throw Error("WebSocket Interceptor: Missing ws-interception-config attribute in the script tag.");var E=JSON.parse(D);if(!E.parentOrigin||typeof E.parentOrigin!=="string")throw Error("WebSocket Interceptor: Invalid parentOrigin in ws-interception-config");
(function(b){var d=Object.getOwnPropertyDescriptor(window,"WebSocket");if(!d||d.writable||d.configurable)d=Object.assign(function(e,h){try{let k=(new URL(e)).hostname;if(b.proxiedDomains.some(m=>k===m||k.endsWith(`.${m}`)))return new B(e,h,b.parentOrigin)}catch(k){throw window.parent.postMessage({type:"websocket_blocked",url:e,reason:"blocked_invalid_url"},b.parentOrigin),new DOMException(`WebSocket connection to '${e}' is not allowed in Canvas.`,"SecurityError");}window.parent.postMessage({type:"websocket_blocked",
url:e,reason:"blocked_domain_not_allowlisted"},b.parentOrigin);throw new DOMException(`WebSocket connection to '${e}' is not allowed in Canvas.`,"SecurityError");},{CONNECTING:0,OPEN:1,CLOSING:2,CLOSED:3}),Object.defineProperty(window,"WebSocket",{value:d,writable:!1,configurable:!1})})({proxiedDomains:E.proxiedDomains||[],parentOrigin:E.parentOrigin});}).call(this);
</script><script data-bard-client-injected="true">((function(modelInformation) {
  const originalFetch = window.fetch;
  // TODO: b/421908508 - Move these out of the script and match all generative AI model calls.
  let googleLlmBaseApiUrls = [
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.textModelName + ':streamGenerateContent',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.textModelName + ':generateContent',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.imageModelName + ':predict',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.imageModelName + ':predictLongRunning',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.imageEditModelName + ':generateContent',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.imageTransformModelName + ':generateContent',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.videoModelName + ':predict',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.videoModelName + ':predictLongRunning',
    'https://generativelanguage.googleapis.com/v1beta/models/' + modelInformation.ttsModelName + ':generateContent',
  ];
  modelInformation.deprecatedTextModelNames.forEach((modelName) => {
    googleLlmBaseApiUrls.push(
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':streamGenerateContent',
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':generateContent',
    );
  });
  modelInformation.deprecatedImageModelNames.forEach((modelName) => {
    googleLlmBaseApiUrls.push(
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':predict',
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':predictLongRunning',
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':generateContent',
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':streamGenerateContent',
    );
  });
  modelInformation.deprecatedGenerateImageModelNames.forEach((modelName) => {
    googleLlmBaseApiUrls.push(
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':generateContent',
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':streamGenerateContent',
    );
  });
  modelInformation.deprecatedImageTransformModelNames.forEach((modelName) => {
    googleLlmBaseApiUrls.push(
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':generateContent',
      'https://generativelanguage.googleapis.com/v1beta/models/' + modelName + ':streamGenerateContent',
    );
  });

  const pendingFetchResolvers = {};
  let nextPromiseId = 0;

  function handleStringInput(input, optionsArgument) {
    const actualUrl = input;
    const fetchCallArgs = [actualUrl, optionsArgument];
    const effectiveOptions = optionsArgument || {};
    const bodyForApiKeyCheck = effectiveOptions.body;
    const bodyForPostMessage = effectiveOptions.body;
    return { actualUrl, fetchCallArgs, effectiveOptions, bodyForApiKeyCheck, bodyForPostMessage };
  }

  function handleRequestInput(input, optionsArgument) {
    const actualUrl = input.url;
    const fetchCallArgs = [input, optionsArgument];
    const effectiveOptions = { method: input.method, headers: new Headers(input.headers) };
    let bodyForApiKeyCheck;
    let bodyForPostMessage;

    if (optionsArgument) {
      if (optionsArgument.method) effectiveOptions.method = optionsArgument.method;
      if (optionsArgument.headers) effectiveOptions.headers = new Headers(optionsArgument.headers);
      if ('body' in optionsArgument) {
        bodyForApiKeyCheck = optionsArgument.body;
        bodyForPostMessage = optionsArgument.body;
      } else {
        bodyForApiKeyCheck = undefined;
        bodyForPostMessage = input.body;
      }
    } else {
      bodyForApiKeyCheck = undefined;
      bodyForPostMessage = input.body;
    }
    return { actualUrl, fetchCallArgs, effectiveOptions, bodyForApiKeyCheck, bodyForPostMessage };
  }

  window.fetch = function(input, optionsArgument) {
    let actualUrl;
    let fetchCallArgs;
    let effectiveOptions = {};
    let bodyForApiKeyCheck;
    let bodyForPostMessage;

    if (typeof input === 'string') {
      ({actualUrl, fetchCallArgs, effectiveOptions, bodyForApiKeyCheck, bodyForPostMessage} = handleStringInput(input, optionsArgument));
    } else if (input instanceof Request) {
      ({actualUrl, fetchCallArgs, effectiveOptions, bodyForApiKeyCheck, bodyForPostMessage} = handleRequestInput(input, optionsArgument));
    } else {
      return originalFetch.apply(window, [input, optionsArgument]);
    }

    effectiveOptions.method = effectiveOptions.method || 'GET';
    if (!effectiveOptions.headers) {
      effectiveOptions.headers = new Headers();
    }


    if (typeof actualUrl === 'string' && googleLlmBaseApiUrls.some((url) => actualUrl.startsWith(url))) {
      let apiKeyIsNull = true;

      const regex = new RegExp("models/([^:]+)");
      const modelNameMatch = actualUrl.match(regex);
      const modelName = modelNameMatch ? modelNameMatch[1] : 'unspecified';


      try {
        const urlObject = new URL(actualUrl);  // Use URL object for robust parsing
        const apiKeyParam = urlObject.searchParams.get('key');
        if (apiKeyParam) {
          apiKeyIsNull = false;
        }
      } catch (e) {
        // Continue checks even if URL parsing fails
      }

      if (apiKeyIsNull && effectiveOptions.headers) {
        const h = new Headers(effectiveOptions.headers);
        const apiKeyHeaderValue = h.get('X-API-Key') || h.get('x-api-key');
        if (apiKeyHeaderValue) {
          apiKeyIsNull = false;
          return originalFetch.apply(window, fetchCallArgs);
        }
      }

      if (apiKeyIsNull && effectiveOptions.method && ['POST', 'PUT', 'PATCH'].includes(effectiveOptions.method.toUpperCase()) && typeof bodyForApiKeyCheck === 'string') {
        try {
          const bodyData = JSON.parse(bodyForApiKeyCheck);
          if (bodyData && bodyData.apiKey) {
            apiKeyIsNull = false;
            return originalFetch.apply(window, fetchCallArgs);
          }
        } catch (e) {
          // Ignore JSON parsing errors
        }
      }

      if(apiKeyIsNull) {
        const promiseId = nextPromiseId++;
        const promise = new Promise((resolve) => {
          pendingFetchResolvers[promiseId] = (resolvedResponse) => {
            delete pendingFetchResolvers[promiseId];
            resolve(resolvedResponse);
          };
        });

        let serializedBodyForPostMessage;
        if (typeof bodyForPostMessage === 'string' || bodyForPostMessage == null) {
            serializedBodyForPostMessage = bodyForPostMessage;
        } else if (bodyForPostMessage instanceof ReadableStream) {
            serializedBodyForPostMessage = null;
        } else {
            try {
                serializedBodyForPostMessage = JSON.stringify(bodyForPostMessage);
            } catch (e) {
                serializedBodyForPostMessage = null;
            }
        }

        const messageOptions = {
            method: effectiveOptions.method,
            headers: Object.fromEntries(new Headers(effectiveOptions.headers).entries()),
            body: serializedBodyForPostMessage
        };

        window.parent.postMessage({
          type: 'requestFetch',
          url: actualUrl,
          modelName: modelName,
          options: messageOptions,
          promiseId: promiseId,
        }, '*');

        return promise;
      }
      return originalFetch.apply(window, fetchCallArgs);
    }
    return originalFetch.apply(window, fetchCallArgs);
  };

  window.addEventListener('message', function(event) {
    if (event.data && event.data.type === 'resolveFetch') {
      const { promiseId, response } = event.data;
      if (pendingFetchResolvers[promiseId]) {
        try {
          const reconstructedResponse = new Response(response.body, {
            status: response.status,
            statusText: response.statusText,
            headers: new Headers(response.headers),
          });
          pendingFetchResolvers[promiseId](reconstructedResponse);
        } catch (error) {
          pendingFetchResolvers[promiseId](new Response(null, { status: 500, statusText: "Interceptor Response Reconstruction Error" }));
        }
      }
    }
  });

}))({"textModelName":"gemini-3-flash-preview","imageModelName":"imagen-4.0-generate-001","imageEditModelName":"gemini-3.1-flash-image","imageTransformModelName":"gemini-3-pro-image","videoModelName":"veo-2.0-generate-001","ttsModelName":"gemini-2.5-flash-preview-tts","deprecatedTextModelNames":["gemini-2.0-flash","gemini-2.5-flash","gemini-2.5-flash-preview-04-17","gemini-2.5-flash-preview-05-20","gemini-2.5-flash-preview-09-2025"],"deprecatedImageModelNames":["imagen-3.0-generate-001","imagen-3.0-generate-002"],"deprecatedGenerateImageModelNames":["gemini-2.5-flash-image-preview","gemini-2.5-flash-image","gemini-3.1-flash-image-preview"],"deprecatedImageTransformModelNames":["gemini-3-pro-image-preview-11-2025"]})</script><script data-bard-client-injected="true">(function() {
  function normalizeSlug(str) {
    try {
      return str
        .trim()
        .toLowerCase()
        .replace(/[^p{L}p{N}s_-]/gu, '')
        .replace(/s+/g, '-');
    } catch (e) {
      return str
        .trim()
        .toLowerCase()
        .replace(/[^a-z0-9s_-]/g, '')
        .replace(/s+/g, '-');
    }
  }

  function findTargetElement(hash) {
    if (!hash || hash === '#') {
      return null;
    }
    const rawId = hash.startsWith('#') ? hash.slice(1) : hash;
    let decodedId = rawId;
    try {
      decodedId = decodeURIComponent(rawId);
    } catch (e) {
      // Ignore URI malformed errors.
    }

    // 1. Direct ID match (raw and decoded).
    let target = document.getElementById(rawId) || document.getElementById(decodedId);
    if (target) {
      return target;
    }

    // 2. Name attribute match (<a name="...">).
    try {
      if (typeof CSS !== 'undefined' && CSS.escape) {
        target =
          document.querySelector('[name="' + CSS.escape(rawId) + '"]') ||
          document.querySelector('[name="' + CSS.escape(decodedId) + '"]');
      } else {
        const namedElements = document.getElementsByName(rawId);
        if (namedElements && namedElements.length > 0) {
          return namedElements[0];
        }
      }
    } catch (e) {
      // Ignore querySelector syntax errors.
    }
    if (target) {
      return target;
    }

    // 3. Match heading text by slug (for Markdown TOCs where headings lack explicit IDs).
    const targetSlug = normalizeSlug(decodedId);
    if (targetSlug) {
      for (const heading of document.querySelectorAll('h1, h2, h3, h4, h5, h6')) {
        if (normalizeSlug(heading.textContent || '') === targetSlug) {
          return heading;
        }
      }
    }

    return null;
  }

  document.addEventListener('click', function(event) {
    const target = event.target;
    const anchor = target && typeof target.closest === 'function' ? target.closest('a') : null;
    if (!anchor) {
      return;
    }

    const href = anchor.getAttribute('href');
    if (
      !href ||
      href.trim().toLowerCase().startsWith('javascript:') ||
      anchor.hasAttribute('download')
    ) {
      return;
    }

    // Check if the link is an in-page hash / anchor link.
    if (href.startsWith('#')) {
      event.preventDefault();
      const targetElement = findTargetElement(href);
      if (targetElement) {
        targetElement.scrollIntoView({behavior: 'smooth', block: 'start'});
      }
      return;
    }

    // Check if the URL has the same origin/pathname but with a hash.
    try {
      const url = new URL(anchor.href, window.location.href);
      if (
        url.hash &&
        url.origin === window.location.origin &&
        url.pathname === window.location.pathname
      ) {
        event.preventDefault();
        const targetElement = findTargetElement(url.hash);
        if (targetElement) {
          targetElement.scrollIntoView({behavior: 'smooth', block: 'start'});
        }
        return;
      }
    } catch (e) {
      // Fall through if URL parsing fails.
    }

    // For all external or full navigation links, prevent iframe-level navigation
    // (which breaks in AGSA WebView or sandboxed iframes) and ensure they open
    // safely in a new tab/window.
    if (anchor.target !== '_blank') {
      event.preventDefault();
      window.open(anchor.href, '_blank', 'noopener,noreferrer');
    }
  }, {capture: true});
})();</script><script data-bard-client-injected="true">(function(){'use strict';function a(){window.parent.postMessage({type:"interaction"},"*")}window.addEventListener("click",a,{capture:!0,passive:!0});window.addEventListener("touchstart",a,{capture:!0,passive:!0});window.addEventListener("keydown",a,{capture:!0,passive:!0});}).call(this);
</script><script data-bard-client-injected="true">(function() {
  const originalConsoleLog = console.log;
  const originalConsoleError = console.error;

    /**
   * Normalizes an error event or a promise rejection reason into a structured error object.
   * @param {*} errorEventOrReason The error object or reason.
   * @return {object} Structured error data { message, name, stack }.
   */
  function getErrorObject(errorEventOrReason) {
    if (errorEventOrReason instanceof Error) {
      return {
        message: errorEventOrReason.message,
        name: errorEventOrReason.name,
        stack: errorEventOrReason.stack,
      };
    }
    // Fallback for non-Error objects.
    try {
      return {
        message: JSON.stringify(errorEventOrReason),
        name: 'UnknownErrorType',
        stack: null,
      };
    } catch (e) {
      return {
        message: String(errorEventOrReason),
        name: 'UnknownErrorTypeNonStringifiable',
        stack: null,
      };
    }
  }

  /**
   * Converts an array of arguments (from log/error) into a single string.
   * Handles Error objects specially to include their message and stack.
   * @param {Array<*>} args - Arguments passed to console methods.
   * @return {string} A string representation of the arguments.
   */
  function stringifyArgs(args) {
    return args
      .map((arg) => {
        if (arg instanceof Error) {
          const {message, stack} = arg;
          return `Error: ${message}${stack ? ('\nStack: ' + stack) : ''}`;
        }
        if (typeof arg === 'object' && arg !== null) {
          try {
            return JSON.stringify(arg);
          } catch (error) {
            return '[Circular Object]';
          }
        } else {
          return String(arg);
        }
      })
      .join(' ');
  }

  console.log = function(...args) {
    const logString = stringifyArgs(args);
    window.parent.postMessage({ type: 'log', message: logString }, '*');
    originalConsoleLog.apply(console, args);
  };

  console.error = function(...args) {
    let errorData;
    if (args.length > 0 && args[0] instanceof Error) {
      const err = args[0];
      // If the first arg is an Error, capture its details.
      errorData = {
        type: 'error',
        source: 'CONSOLE_ERROR',
        ...getErrorObject(err),
        rawArgsString: stringifyArgs(args.slice(1)),
        timestamp: new Date().toISOString(),
      };
    } else {
      // If not an Error object, treat all args as a general error message.
      errorData = {
        type: 'error',
        source: 'CONSOLE_ERROR',
        message: stringifyArgs(args),
        name: 'ConsoleLoggedError',
        stack: null,
        timestamp: new Date().toISOString(),
      };
    }
    window.parent.postMessage(errorData, '*');
    originalConsoleError.apply(console, args);
  };

  // Listen for global unhandled synchronous errors.
  window.addEventListener('error', function(event) {
    const errorDetails = event.error ? getErrorObject(event.error) : {
      message: event.message,
      name: 'GlobalError',
      stack: null,
      filename: event.filename,
      lineno: event.lineno,
      colno: event.colno,
    };

    window.parent.postMessage({
      type: 'error',
      source: 'global',
      ...errorDetails,
      message: errorDetails.message || event.message,
      timestamp: new Date().toISOString(),
    }, '*');
  });

  // Listen for unhandled promise rejections (asynchronous errors).
  window.addEventListener('unhandledrejection', function(event) {
    const errorDetails = getErrorObject(event.reason);

    window.parent.postMessage({
      type: 'error',
      source: 'unhandledrejection',
      ...errorDetails,
      message: errorDetails.message || 'Unhandled Promise Rejection',
      timestamp: new Date().toISOString(),
    }, '*');
  });

})();</script>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>Activity Hub</title>
  
  <!-- Метатеги полноценного мобильного приложения для Android и iOS -->
  <meta name="theme-color" content="#0b0f19">
  <meta name="mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-capable" content="yes">
  <meta name="apple-mobile-web-app-status-bar-style" content="black-translucent">
  <meta name="apple-mobile-web-app-title" content="Activity Hub">
  <link rel="icon" type="image/svg+xml" href="data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'%3E%3Crect width='100' height='100' rx='25' fill='%230f172a'/%3E%3Cpath d='M50 15 L25 55 L48 55 L42 85 L75 45 L52 45 Z' fill='%2338bdf8'/%3E%3C/svg%3E">

  <style>
    :root {
      --bg-main: #0b0f19;
      --bg-card: #151e2e;
      --bg-elevated: #1e293b;
      --border-color: #334155;
      --text-main: #f8fafc;
      --text-muted: #94a3b8;
      --accent-blue: #3b82f6;
      --accent-green: #22c55e;
      --accent-red: #ef4444;
      --accent-orange: #f59e0b;
      --accent-cyan: #38bdf8;
      --radius-sm: 6px;
      --radius-md: 10px;
      --radius-lg: 14px;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      -webkit-tap-highlight-color: transparent;
      font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif;
    }

    body {
      background-color: var(--bg-main);
      color: var(--text-main);
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      padding-bottom: 30px;
    }

    /* Шапка приложения */
    header {
      background: var(--bg-card);
      border-bottom: 1px solid var(--border-color);
      padding: 12px 16px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      position: sticky;
      top: 0;
      z-index: 50;
    }

    .brand-title {
      font-size: 18px;
      font-weight: 800;
      color: var(--text-main);
      display: flex;
      align-items: center;
      gap: 8px;
      letter-spacing: -0.5px;
    }

    .brand-title span {
      color: var(--accent-cyan);
    }

    /* Навигационные вкладки */
    .tabs-nav {
      display: flex;
      gap: 6px;
      padding: 8px 12px;
      background: var(--bg-card);
      border-bottom: 1px solid var(--border-color);
      overflow-x: auto;
      white-space: nowrap;
    }

    .tab-btn {
      background: transparent;
      border: 1px solid transparent;
      color: var(--text-muted);
      padding: 8px 14px;
      font-size: 13px;
      font-weight: 600;
      border-radius: var(--radius-sm);
      cursor: pointer;
      transition: all 0.2s;
    }

    .tab-btn.active {
      background: var(--bg-elevated);
      color: var(--text-main);
      border-color: var(--border-color);
    }

    /* Контейнер */
    .container {
      width: 100%;
      max-width: 1300px;
      margin: 0 auto;
      padding: 14px;
      flex: 1;
    }

    .tab-content {
      display: none;
    }

    .tab-content.active {
      display: block;
    }

    /* Карточки */
    .card {
      background: var(--bg-card);
      border: 1px solid var(--border-color);
      border-radius: var(--radius-lg);
      padding: 16px;
      margin-bottom: 16px;
    }

    .card-title {
      font-size: 15px;
      font-weight: 700;
      color: var(--text-main);
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    /* Кнопки */
    .action-btn {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      width: 100%;
      padding: 14px;
      border-radius: var(--radius-md);
      font-size: 15px;
      font-weight: 700;
      border: none;
      cursor: pointer;
      transition: transform 0.1s, opacity 0.2s;
    }

    .action-btn:active {
      transform: scale(0.98);
      opacity: 0.9;
    }

    .btn-start {
      background: linear-gradient(135deg, #2563eb, #1d4ed8);
      color: #fff;
      box-shadow: 0 4px 14px rgba(37, 99, 235, 0.4);
    }

    .btn-stop {
      background: linear-gradient(135deg, #dc2626, #b91c1c);
      color: #fff;
      box-shadow: 0 4px 14px rgba(220, 38, 38, 0.4);
    }

    /* Сегментированный переключатель СТАРТ / ЗАВЕРШЕНИЕ */
    .shift-toggle-container {
      display: flex;
      background: rgba(15, 23, 42, 0.85);
      border: 1px solid rgba(51, 65, 85, 0.8);
      border-radius: 14px;
      padding: 4px;
      gap: 6px;
      margin-bottom: 14px;
      box-shadow: inset 0 2px 4px rgba(0, 0, 0, 0.4);
    }

    .shift-mode-btn {
      flex: 1;
      padding: 12px 16px;
      font-size: 13px;
      font-weight: 800;
      letter-spacing: 0.6px;
      text-transform: uppercase;
      border-radius: 10px;
      border: 1px solid transparent;
      background: transparent;
      color: #64748b;
      cursor: pointer;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 8px;
      transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
    }

    .shift-mode-btn .mode-dot {
      width: 7px;
      height: 7px;
      border-radius: 50%;
      background: #475569;
      transition: all 0.25s ease;
    }

    .shift-mode-btn.active#modeStartBtn {
      background: linear-gradient(135deg, rgba(2, 132, 199, 0.25), rgba(37, 99, 235, 0.35));
      color: #38bdf8;
      border-color: rgba(56, 189, 248, 0.5);
      box-shadow: 0 4px 14px rgba(2, 132, 199, 0.25), inset 0 1px 0 rgba(255, 255, 255, 0.1);
    }

    .shift-mode-btn.active#modeStartBtn .mode-dot {
      background: #38bdf8;
      box-shadow: 0 0 8px #38bdf8;
    }

    .shift-mode-btn.active#modeStopBtn {
      background: linear-gradient(135deg, rgba(220, 38, 38, 0.22), rgba(185, 28, 28, 0.32));
      color: #f87171;
      border-color: rgba(239, 68, 68, 0.5);
      box-shadow: 0 4px 14px rgba(220, 38, 38, 0.25), inset 0 1px 0 rgba(255, 255, 255, 0.1);
    }

    .shift-mode-btn.active#modeStopBtn .mode-dot {
      background: #ef4444;
      box-shadow: 0 0 8px #ef4444;
    }

    /* Поля ввода */
    .custom-input, .custom-select {
      background: var(--bg-elevated);
      border: 1px solid var(--border-color);
      color: var(--text-main);
      padding: 10px 12px;
      border-radius: var(--radius-sm);
      font-size: 14px;
      width: 100%;
      outline: none;
    }

    .custom-input:focus, .custom-select:focus {
      border-color: var(--accent-cyan);
    }

    /* Статус синхронизации */
    .cloud-status-badge {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 4px 10px;
      border-radius: 20px;
      font-size: 11px;
      font-weight: 600;
      background: rgba(30, 41, 59, 0.8);
      border: 1px solid var(--border-color);
      color: var(--text-muted);
      transition: all 0.2s ease;
    }
    .cloud-status-badge.online {
      border-color: #22c55e;
      color: #86efac;
    }
    .cloud-status-badge.offline {
      border-color: #eab308;
      color: #fde047;
    }

    /* Список сотрудников в карточке */
    .workers-selection-list {
      display: flex;
      flex-direction: column;
      gap: 8px;
      max-height: 480px;
      overflow-y: auto;
      padding-right: 4px;
      contain: content;
    }

    .worker-card {
      background: var(--bg-elevated);
      border: 1px solid var(--border-color);
      border-radius: var(--radius-md);
      padding: 12px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      cursor: pointer;
      user-select: none;
      transition: border-color 0.15s ease, background 0.15s ease, transform 0.1s ease;
      will-change: transform;
    }

    .worker-card.checked {
      border-color: #38bdf8;
      background: linear-gradient(135deg, rgba(56, 189, 248, 0.16), rgba(30, 41, 59, 0.95));
      box-shadow: 0 0 12px rgba(56, 189, 248, 0.25);
    }

    .worker-card.on-shift {
      border-left: 4px solid var(--accent-green);
    }

    .worker-name {
      font-size: 14px;
      font-weight: 700;
      color: var(--text-main);
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 4px;
    }

    /* Интерактивная кнопка выбора */
    .custom-checkbox {
      display: inline-flex;
      align-items: center;
      gap: 6px;
      padding: 7px 14px;
      border-radius: 20px;
      border: 1.5px solid #334155;
      background: linear-gradient(180deg, #1e293b 0%, #0f172a 100%);
      color: #94a3b8;
      font-size: 12px;
      font-weight: 700;
      letter-spacing: 0.3px;
      flex-shrink: 0;
      cursor: pointer;
      transition: all 0.25s cubic-bezier(0.4, 0, 0.2, 1);
      box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.05), 0 2px 4px rgba(0, 0, 0, 0.3);
    }

    .custom-checkbox .chk-icon {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      width: 18px;
      height: 18px;
      border-radius: 50%;
      background: rgba(148, 163, 184, 0.15);
      color: #94a3b8;
      font-size: 11px;
      transition: all 0.25s ease;
    }

    .worker-card:hover .custom-checkbox {
      border-color: #64748b;
      color: #cbd5e1;
    }

    .worker-card.checked .custom-checkbox {
      border-color: #38bdf8;
      background: linear-gradient(135deg, #0284c7 0%, #2563eb 100%);
      color: #ffffff;
      box-shadow: 0 0 14px rgba(56, 189, 248, 0.45), inset 0 1px 1px rgba(255, 255, 255, 0.3);
      transform: translateY(-1px);
    }

    .worker-card.checked .custom-checkbox .chk-icon {
      background: rgba(255, 255, 255, 0.25);
      color: #ffffff;
    }

    /* Таблицы */
    .table-responsive {
      width: 100%;
      overflow-x: auto;
      border-radius: var(--radius-md);
      border: 1px solid var(--border-color);
    }

    .matrix-table {
      width: 100%;
      border-collapse: collapse;
      font-size: 12px;
      text-align: center;
      background: var(--bg-card);
      min-width: 800px;
    }

    .matrix-table th, .matrix-table td {
      border: 1px solid var(--border-color);
      padding: 6px 8px;
    }

    .matrix-table th {
      background: #0f172a;
      color: var(--text-muted);
      font-weight: 700;
      position: sticky;
      top: 0;
    }

    .sticky-col-1 {
      position: sticky;
      left: 0;
      background: var(--bg-card);
      font-weight: 700;
      text-align: left;
      z-index: 10;
      min-width: 160px;
    }

    .sticky-col-2 {
      position: sticky;
      left: 160px;
      background: var(--bg-card);
      color: var(--text-muted);
      text-align: left;
      z-index: 10;
      min-width: 120px;
    }

    .sticky-col-3 {
      position: sticky;
      left: 280px;
      background: var(--bg-elevated);
      font-weight: 700;
      z-index: 10;
      min-width: 100px;
    }

    .weekend-col {
      background: rgba(239, 68, 68, 0.08);
    }

    .summary-cell {
      font-weight: 700;
      background: #0f172a;
    }

    .editable-day {
      cursor: pointer;
    }

    .editable-day:hover {
      background: rgba(59, 130, 246, 0.2);
    }

    /* Модальные окна */
    .modal-overlay {
      position: fixed;
      inset: 0;
      background: rgba(0, 0, 0, 0.75);
      display: none;
      align-items: center;
      justify-content: center;
      z-index: 100;
      padding: 16px;
    }

    .modal-overlay.open {
      display: flex;
    }

    .modal-box {
      background: var(--bg-card);
      border: 1px solid var(--border-color);
      border-radius: var(--radius-lg);
      padding: 20px;
      width: 100%;
      max-width: 500px;
      display: flex;
      flex-direction: column;
      gap: 12px;
      max-height: 90vh;
      overflow-y: auto;
    }

    .modal-title {
      font-size: 16px;
      font-weight: 800;
      color: var(--text-main);
    }

    /* Тосты */
    #toastMessage {
      position: fixed;
      bottom: 24px;
      left: 50%;
      transform: translateX(-50%);
      background: #0f172a;
      border: 1px solid var(--border-color);
      box-shadow: 0 10px 25px rgba(0,0,0,0.5);
      color: #fff;
      padding: 10px 18px;
      border-radius: 30px;
      font-size: 13px;
      font-weight: 600;
      display: none;
      z-index: 200;
      text-align: center;
      max-width: 90%;
    }

    @media (max-width: 768px) {
      .hide-mobile {
        display: none !important;
      }
      .foreman-add-grid {
        grid-template-columns: 1fr !important;
      }
    }
  </style>
</head>
<body>

  <!-- ШАПКА -->
  <header>
    <div class="brand-title">
      ⚡ <span>Activity Hub</span>
      <span id="cloudStatusIndicator" class="cloud-status-badge online" style="margin-left: 10px; cursor: pointer;" onclick="checkCloudConnectionNow()" title="Нажмите для проверки связи"><span class="status-dot">🟢</span> Облако онлайн</span>
    </div>
    <div style="display: flex; gap: 8px;">
      <button id="btnDownloadHtml" class="action-btn hide-mobile" style="width: auto; padding: 6px 12px; font-size: 12px; background: #059669; color: #fff;" onclick="downloadThisHtmlFile()">
        💾 Скачать index.html
      </button>
    </div>
  </header>

  <!-- ВКЛАДКИ -->
  <div class="tabs-nav" id="mainTabsNav">
    <button class="tab-btn active" id="tabBtnForeman" onclick="switchTab('foreman')">📱 Ответственный</button>
    <button class="tab-btn" id="tabBtnDocs" onclick="switchTab('docs')">📷 Фотоотчет и Чеки</button>
    <button class="tab-btn" id="tabBtnMatrix" onclick="switchTab('matrix')">📊 Табель</button>
    <button class="tab-btn" id="tabBtnRates" onclick="switchTab('rates')">🔑 Админка</button>
  </div>

  <div class="container">

    <!-- ВКЛАДКА 1: МОБИЛЬНЫЙ ПУЛЬТ ДЛЯ ОТВЕТСТВЕННОГО -->
    <div id="tab-foreman" class="tab-content active">
      <div class="card" style="max-width: 600px; margin: 0 auto;">
        
        <!-- Верхняя плашка статуса -->
        <div style="background: linear-gradient(135deg, #1e293b, #0f172a); border: 1px solid var(--border-color); border-radius: var(--radius-md); padding: 12px 14px; margin-bottom: 12px; display: flex; justify-content: space-between; align-items: center;">
          <div>
            <div style="font-size: 11px; text-transform: uppercase; color: var(--text-muted); font-weight: 700; letter-spacing: 0.5px;">Рабочая смена (Самозанятые)</div>
            <div style="font-size: 14px; font-weight: 700; color: #f8fafc; margin-top: 1px;" id="liveDateDisplay">6 Ноября 2026 (ПТ)</div>
          </div>
          <div style="text-align: right;">
            <div style="font-size: 11px; color: var(--text-muted);">Ответственный:</div>
            <div style="display: flex; align-items: center; gap: 4px; justify-content: flex-end;">
              <div style="font-size: 13px; font-weight: 700; color: #38bdf8;" id="currentForemanDisplay">На площадке</div>
              <button onclick="openSwitchForemanModal()" style="background: rgba(56, 189, 248, 0.15); border: 1px solid #0284c7; color: #38bdf8; border-radius: 6px; font-size: 10px; padding: 2px 6px; cursor: pointer; font-weight: bold;" title="Сменить ответственного">⇄</button>
            </div>
          </div>
        </div>

        <!-- Кнопка быстрой установки приложения на Android (PWA) -->
        <div id="pwaInstallPromptBox" style="display: none; background: linear-gradient(135deg, rgba(2, 132, 199, 0.2), rgba(15, 23, 42, 0.9)); border: 1.5px solid #0284c7; border-radius: var(--radius-md); padding: 10px 12px; margin-bottom: 12px; align-items: center; justify-content: space-between; gap: 8px;">
          <div style="font-size: 12px; color: #e0f2fe;">
            📲 <b>Установить на рабочий стол:</b> открывать приложение без браузера
          </div>
          <button class="action-btn" style="width: auto; padding: 6px 12px; font-size: 11px; background: #0284c7; color: #fff; white-space: nowrap;" onclick="triggerPwaInstall()">
            Установить
          </button>
        </div>

        <!-- Переключатель СТАРТ / ЗАВЕРШЕНИЕ -->
        <div class="shift-toggle-container">
          <button id="modeStartBtn" class="shift-mode-btn active" onclick="setShiftMode('start')">
            <span class="mode-dot"></span>
            <span>СТАРТ СМЕНЫ</span>
          </button>
          <button id="modeStopBtn" class="shift-mode-btn" onclick="setShiftMode('stop')">
            <span class="mode-dot"></span>
            <span>ЗАВЕРШЕНИЕ</span>
          </button>
        </div>

        <!-- Время на объекте -->
        <div style="background: rgba(30, 41, 59, 0.7); border: 1px solid var(--border-color); border-radius: var(--radius-md); padding: 10px 12px; margin-bottom: 12px;">
          <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 6px;">
            <label style="font-size: 12px; font-weight: 600; color: #94a3b8;" id="declaredTimeLabel">🕒 Время начала работы:</label>
          </div>
          <div style="display: flex; gap: 8px; align-items: center;">
            <input type="time" id="declaredTimeInput" class="custom-input" style="font-size: 18px; font-weight: 700; padding: 8px 12px; max-width: 150px; text-align: center; color: #38bdf8; background: #0f172a; border-color: #3b82f6;">
            <span style="font-size: 12px; color: var(--text-muted); line-height: 1.3;" id="declaredTimeHint"></span>
          </div>
        </div>

        <!-- Быстрая кнопка фото документов -->
        <div style="margin-bottom: 12px;">
          <input type="file" id="universalDocFileInput" accept="image/*" capture="camera" style="display: none;" onchange="handleUniversalDocUpload(event)">
          <button class="action-btn" style="background: #334155; border: 1px solid #475569; color: #f8fafc; font-size: 13px; padding: 11px 14px;" onclick="document.getElementById('universalDocFileInput').click()">
            📸 + ФОТООТЧЕТ И ЧЕКИ
          </button>
        </div>

        <!-- Предупреждение о сбое сети (если домен Vercel виснет в таймауте) -->
        <div id="netStatusAlert" style="display: none; background: rgba(239, 68, 68, 0.15); border: 1px solid #ef4444; border-radius: var(--radius-sm); padding: 8px 12px; margin-bottom: 12px; font-size: 12px; color: #fca5a5;">
          ⚠️ Сервер Vercel недоступен на этом операторе связи. Приложение работает автономно! Все смены сохраняются на телефоне.
        </div>

        <!-- Добавление человека прямо на площадке (ТОЛЬКО НА СТАРТЕ) -->
        <div id="foremanAddWorkerBlock" style="background: linear-gradient(135deg, rgba(16, 185, 129, 0.12), rgba(15, 23, 42, 0.95)); border: 1.5px solid rgba(16, 185, 129, 0.45); border-radius: var(--radius-md); padding: 12px; margin-bottom: 14px; box-shadow: 0 4px 18px rgba(16, 185, 129, 0.08);">
          <div style="display: flex; align-items: center; justify-content: space-between; margin-bottom: 8px;">
            <div style="display: flex; align-items: center; gap: 6px; font-size: 12px; font-weight: 800; color: #6ee7b7; text-transform: uppercase; letter-spacing: 0.5px;">
              <span style="display: inline-flex; align-items: center; justify-content: center; width: 18px; height: 18px; background: #059669; color: #fff; border-radius: 50%; font-size: 12px;">+</span>
              Добавить самозанятого на объекте
            </div>
          </div>
          <div style="display: flex; gap: 6px; margin-bottom: 6px;">
            <input type="text" id="quickWorkerName" class="custom-input" placeholder="ФИО самозанятого" style="flex: 2; font-size: 13px; padding: 8px 10px; background: rgba(15, 23, 42, 0.85); border-color: rgba(16, 185, 129, 0.35);">
            <input type="text" id="quickWorkerRole" class="custom-input" placeholder="Специальность" style="flex: 1.5; font-size: 13px; padding: 8px 10px; background: rgba(15, 23, 42, 0.85); border-color: rgba(16, 185, 129, 0.35);">
          </div>
          <div style="display: flex; gap: 6px;">
            <input type="tel" id="quickWorkerPhone" class="custom-input" placeholder="Телефон / Номер" style="flex: 2; font-size: 13px; padding: 8px 10px; background: rgba(15, 23, 42, 0.85); border-color: rgba(16, 185, 129, 0.35);">
            <button class="action-btn" style="flex: 1; padding: 8px 12px; font-size: 13px; font-weight: 700; background: linear-gradient(135deg, #059669, #047857); border: 1px solid #10b981; color: #fff; box-shadow: 0 2px 8px rgba(5, 150, 105, 0.35);" onclick="addWorkerByForeman()">OK</button>
          </div>
        </div>

        <!-- Выбор объекта -->
        <div style="background: linear-gradient(135deg, rgba(30, 58, 138, 0.35), rgba(15, 23, 42, 0.95)); border: 1.5px solid #3b82f6; border-radius: var(--radius-md); padding: 14px; margin-bottom: 14px; box-shadow: 0 4px 18px rgba(37, 99, 235, 0.18);">
          <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px;">
            <div style="display: flex; align-items: center; gap: 7px; font-size: 13px; font-weight: 800; color: #60a5fa; text-transform: uppercase; letter-spacing: 0.5px;">
              <span>📍</span> ОБЪЕКТ ВЫПОЛНЕНИЯ РАБОТ
            </div>
          </div>

          <div style="display: flex; gap: 8px; align-items: stretch;">
            <div style="flex: 1; position: relative;">
              <select id="foremanObjectSelect" class="custom-select" style="width: 100%; height: 100%; font-size: 14px; font-weight: 700; color: #f8fafc; background: #0f172a; border: 1.5px solid #3b82f6; padding: 10px 12px; border-radius: var(--radius-sm);" onchange="changeForemanObject()"><option value="Сухарка">Сухарка</option></select>
            </div>
            <button class="action-btn" style="width: auto; padding: 10px 14px; font-size: 13px; font-weight: 800; background: linear-gradient(135deg, #2563eb, #1d4ed8); border: 1px solid #60a5fa; color: #ffffff; white-space: nowrap; box-shadow: 0 2px 10px rgba(37, 99, 235, 0.35);" onclick="addNewObjectPrompt()">
              ✨ + Новый объект
            </button>
          </div>
        </div>

        <!-- Баннер активной смены -->
        <div id="liveShiftActiveBanner" style="display: none; background: linear-gradient(135deg, rgba(34, 197, 94, 0.15), rgba(15, 23, 42, 0.9)); border: 1px solid #22c55e; border-radius: var(--radius-md); padding: 10px 14px; margin-bottom: 12px; justify-content: space-between; align-items: center;">
          <div>
            <div style="font-size: 11px; text-transform: uppercase; color: #86efac; font-weight: 700; letter-spacing: 0.5px;">🟢 Смена активна</div>
            <div style="font-size: 12px; color: var(--text-muted);" id="liveShiftCountText">На объекте: 0 чел.</div>
          </div>
          <div style="text-align: right;">
            <div style="font-size: 11px; color: #94a3b8;">Идёт отсчёт:</div>
            <div style="font-size: 16px; font-weight: 800; font-family: monospace; color: #4ade80;" id="liveShiftGlobalTimer">00:00:00</div>
          </div>
        </div>

        <!-- Список сотрудников -->
        <div style="background: linear-gradient(180deg, rgba(30, 41, 59, 0.5), rgba(15, 23, 42, 0.85)); border: 1.5px solid #334155; border-radius: var(--radius-md); padding: 14px; margin-bottom: 14px; box-shadow: 0 4px 16px rgba(0, 0, 0, 0.3);">
          <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; border-bottom: 1px solid rgba(51, 65, 85, 0.6); padding-bottom: 8px;">
            <div style="display: flex; align-items: center; gap: 8px; font-size: 14px; font-weight: 800; color: #f1f5f9; letter-spacing: 0.3px;">
              <span style="font-size: 16px;">👥</span> Сотрудники
            </div>
            <span style="font-size: 11px; color: #94a3b8; background: #0f172a; border: 1px solid #334155; padding: 2px 8px; border-radius: 12px;">Нажмите на карточку</span>
          </div>
          <div class="workers-selection-list" id="workersListMobile"><div class="worker-card  ">
          <div style="flex: 1; padding-right: 8px;">
            <div class="worker-name">
              <span>Дмитрий</span>
              <span style="font-size: 10px; padding: 2px 6px; border-radius: 4px; background: #f59e0b; color: #000; font-weight: 800;">Оператор ЭП</span>
              
            </div>
            
            
          </div>
          <div style="display: flex; align-items: center; gap: 4px;">
            
            <div class="custom-checkbox">
              <span class="chk-icon">+</span>
              <span>Выбрать</span>
            </div>
          </div>
        </div><div class="worker-card  ">
          <div style="flex: 1; padding-right: 8px;">
            <div class="worker-name">
              <span>Роман</span>
              <span style="font-size: 10px; padding: 2px 6px; border-radius: 4px; background: #ef4444; color: #fff; font-weight: 800;">Оператор ГНБ</span>
              
            </div>
            
            
          </div>
          <div style="display: flex; align-items: center; gap: 4px;">
            
            <div class="custom-checkbox">
              <span class="chk-icon">+</span>
              <span>Выбрать</span>
            </div>
          </div>
        </div><div class="worker-card  ">
          <div style="flex: 1; padding-right: 8px;">
            <div class="worker-name">
              <span>Маршит</span>
              <span style="font-size: 10px; padding: 2px 6px; border-radius: 4px; background: #f59e0b; color: #000; font-weight: 800;">Оператор ЭП</span>
              
            </div>
            
            
          </div>
          <div style="display: flex; align-items: center; gap: 4px;">
            
            <div class="custom-checkbox">
              <span class="chk-icon">+</span>
              <span>Выбрать</span>
            </div>
          </div>
        </div><div class="worker-card  ">
          <div style="flex: 1; padding-right: 8px;">
            <div class="worker-name">
              <span>Николай</span>
              <span style="font-size: 10px; padding: 2px 6px; border-radius: 4px; background: #f59e0b; color: #000; font-weight: 800;">Оператор ЭП</span>
              
            </div>
            
            
          </div>
          <div style="display: flex; align-items: center; gap: 4px;">
            
            <div class="custom-checkbox">
              <span class="chk-icon">+</span>
              <span>Выбрать</span>
            </div>
          </div>
        </div><div class="worker-card  ">
          <div style="flex: 1; padding-right: 8px;">
            <div class="worker-name">
              <span>Гномыч</span>
              <span style="font-size: 10px; padding: 2px 6px; border-radius: 4px; background: #22c55e; color: #000; font-weight: 800;">Слесарь</span>
              
            </div>
            
            
          </div>
          <div style="display: flex; align-items: center; gap: 4px;">
            
            <div class="custom-checkbox">
              <span class="chk-icon">+</span>
              <span>Выбрать</span>
            </div>
          </div>
        </div></div>
        </div>

        <!-- Главная кнопка действия -->
        <button id="mainActionBtn" class="action-btn btn-start" onclick="executeShiftAction()">
          <span>НАЧАТЬ СМЕНУ</span>
        </button>

        <!-- Кнопка «Я ошибся» -->
        <button id="btnForemanMistake" class="action-btn" style="display: none; margin-top: 8px; padding: 12px; font-size: 13px; background: #334155; border: 1.5px dashed #f59e0b; color: #fde047;" onclick="openMistakeModal()">
          ⚠️ Я ОШИБСЯ / ВНЕСТИ УТОЧНЕНИЕ
        </button>

      </div>
    </div>

    <!-- ВКЛАДКА 2: ДОКУМЕНТЫ & ЧЕКИ -->
    <div id="tab-docs" class="tab-content">
      <div class="card">
        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px; flex-wrap: wrap; gap: 8px;">
          <div>
            <div class="card-title" style="margin-bottom: 2px;">📷 Фотоотчет и Чеки</div>
            <div style="font-size: 12px; color: var(--text-muted);">
              Снимки документов и чеков с автоматической привязкой объекта, даты и ответственного лица.
            </div>
          </div>
          <button class="action-btn hide-mobile" style="width: auto; padding: 6px 12px; font-size: 12px; background: #334155;" onclick="exportDocsToCsv()">
            📥 Экспорт списка (CSV)
          </button>
        </div>

        <div class="table-responsive">
          <table class="matrix-table" style="font-size: 13px;">
            <thead>
              <tr>
                <th style="width: 60px;">№</th>
                <th style="width: 140px;">Дата / Время</th>
                <th>Объект</th>
                <th>Ответственный</th>
                <th style="width: 100px;">Фото</th>
                <th style="width: 80px;">Действие</th>
              </tr>
            </thead>
            <tbody id="universalDocsTableBody"><tr><td colspan="6" style="padding: 20px; color: var(--text-muted);">Нет прикреплённых документов</td></tr></tbody>
          </table>
        </div>
      </div>
    </div>

    <!-- ВКЛАДКА 3: ТАБЕЛЬ УЧЕТА СМЕН -->
    <div id="tab-matrix" class="tab-content">
      <div class="card">
        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 12px; flex-wrap: wrap; gap: 8px;">
          <div style="display: flex; align-items: center; gap: 10px;">
            <button class="action-btn" style="width: auto; padding: 6px 12px; background: var(--bg-elevated);" onclick="changeMonth(-1)">◀</button>
            <div style="font-size: 16px; font-weight: 800; color: #38bdf8;" id="matrixMonthLabel">Ноябрь 2026</div>
            <button class="action-btn" style="width: auto; padding: 6px 12px; background: var(--bg-elevated);" onclick="changeMonth(1)">▶</button>
          </div>
          <button id="btnExportCsv" class="action-btn hide-mobile" style="width: auto; padding: 6px 12px; font-size: 12px; background: #059669; color: #fff;" onclick="exportMatrixToCsv()">
            📥 Выгрузить Excel (.xls)
          </button>
        </div>

        <div style="font-size: 12px; color: var(--text-muted); margin-bottom: 8px;">
          Табель самозанятого стартует строго с месяца его первого выхода на работу. Итоговые показатели: Часы и Заработок.
        </div>

        <div class="table-responsive">
          <table class="matrix-table" id="fullMatrixTable"><thead><tr><th class="sticky-col-1">ФИО Исполнителя</th><th class="sticky-col-2">Специальность</th><th class="sticky-col-3">Показатель</th><th class="weekend-col">1</th><th class="">2</th><th class="">3</th><th class="">4</th><th class="">5</th><th class="">6</th><th class="weekend-col">7</th><th class="weekend-col">8</th><th class="">9</th><th class="">10</th><th class="">11</th><th class="">12</th><th class="">13</th><th class="weekend-col">14</th><th class="weekend-col">15</th><th class="">16</th><th class="">17</th><th class="">18</th><th class="">19</th><th class="">20</th><th class="weekend-col">21</th><th class="weekend-col">22</th><th class="">23</th><th class="">24</th><th class="">25</th><th class="">26</th><th class="">27</th><th class="weekend-col">28</th><th class="weekend-col">29</th><th class="">30</th><th class="summary-cell">ИТОГО</th></tr></thead><tbody><tr><td rowspan="5" class="sticky-col-1">Дмитрий</td><td rowspan="5" class="sticky-col-2">Оператор ЭП</td><td class="sticky-col-3" style="color: #38bdf8;">Часы</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-01', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-02', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-03', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-04', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-05', 'f_1793895782377')">10</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-06', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-07', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-08', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-09', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-10', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-11', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-12', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-13', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-14', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-15', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-16', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-17', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-18', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-19', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-20', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-21', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-22', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-23', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-24', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-25', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-26', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-27', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-28', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-29', 'f_1793895782377')">·</td><td class="editable-day" onclick="openShiftEditModal('Дмитрий', '2026-11-30', 'f_1793895782377')">·</td><td class="summary-cell" style="color: #38bdf8;">10.0 ч</td></tr><tr><td class="sticky-col-3" style="color: #94a3b8;">Объект</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">Сухарка</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #c084fc;">Ответственный</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="Отписал: Дмитрий">Дмитрий</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #fde047;">Уточнения</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #4ade80;">Заработок</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">8500</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td class="summary-cell" style="color: #4ade80;">8&nbsp;500 ₽</td></tr><tr><td rowspan="5" class="sticky-col-1">Роман</td><td rowspan="5" class="sticky-col-2">Оператор ГНБ</td><td class="sticky-col-3" style="color: #38bdf8;">Часы</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-01', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-02', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-03', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-04', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-05', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-06', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-07', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-08', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-09', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-10', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-11', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-12', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-13', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-14', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-15', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-16', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-17', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-18', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-19', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-20', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-21', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-22', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-23', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-24', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-25', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-26', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-27', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-28', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-29', 'f_1793895796577')">·</td><td class="editable-day" onclick="openShiftEditModal('Роман', '2026-11-30', 'f_1793895796577')">·</td><td class="summary-cell" style="color: #38bdf8;">0.0 ч</td></tr><tr><td class="sticky-col-3" style="color: #94a3b8;">Объект</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #c084fc;">Ответственный</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #fde047;">Уточнения</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #4ade80;">Заработок</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td class="summary-cell" style="color: #4ade80;">0 ₽</td></tr><tr><td rowspan="5" class="sticky-col-1">Маршит</td><td rowspan="5" class="sticky-col-2">Оператор ЭП</td><td class="sticky-col-3" style="color: #38bdf8;">Часы</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-01', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-02', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-03', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-04', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-05', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-06', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-07', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-08', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-09', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-10', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-11', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-12', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-13', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-14', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-15', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-16', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-17', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-18', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-19', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-20', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-21', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-22', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-23', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-24', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-25', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-26', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-27', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-28', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-29', 'f_1793895806521')">·</td><td class="editable-day" onclick="openShiftEditModal('Маршит', '2026-11-30', 'f_1793895806521')">·</td><td class="summary-cell" style="color: #38bdf8;">0.0 ч</td></tr><tr><td class="sticky-col-3" style="color: #94a3b8;">Объект</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #c084fc;">Ответственный</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #fde047;">Уточнения</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #4ade80;">Заработок</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td class="summary-cell" style="color: #4ade80;">0 ₽</td></tr><tr><td rowspan="5" class="sticky-col-1">Николай</td><td rowspan="5" class="sticky-col-2">Оператор ЭП</td><td class="sticky-col-3" style="color: #38bdf8;">Часы</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-01', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-02', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-03', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-04', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-05', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-06', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-07', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-08', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-09', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-10', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-11', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-12', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-13', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-14', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-15', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-16', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-17', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-18', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-19', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-20', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-21', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-22', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-23', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-24', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-25', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-26', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-27', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-28', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-29', 'f_1793895829681')">·</td><td class="editable-day" onclick="openShiftEditModal('Николай', '2026-11-30', 'f_1793895829681')">·</td><td class="summary-cell" style="color: #38bdf8;">0.0 ч</td></tr><tr><td class="sticky-col-3" style="color: #94a3b8;">Объект</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #c084fc;">Ответственный</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #fde047;">Уточнения</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #4ade80;">Заработок</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td class="summary-cell" style="color: #4ade80;">0 ₽</td></tr><tr><td rowspan="5" class="sticky-col-1">Гномыч</td><td rowspan="5" class="sticky-col-2">Слесарь</td><td class="sticky-col-3" style="color: #38bdf8;">Часы</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-01', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-02', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-03', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-04', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-05', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-06', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-07', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-08', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-09', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-10', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-11', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-12', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-13', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-14', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-15', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-16', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-17', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-18', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-19', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-20', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-21', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-22', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-23', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-24', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-25', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-26', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-27', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-28', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-29', 'f_1793959015828')">·</td><td class="editable-day" onclick="openShiftEditModal('Гномыч', '2026-11-30', 'f_1793959015828')">·</td><td class="summary-cell" style="color: #38bdf8;">0.0 ч</td></tr><tr><td class="sticky-col-3" style="color: #94a3b8;">Объект</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td style="font-size: 10px; color: #94a3b8;">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #c084fc;">Ответственный</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #fde047;">Уточнения</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td style="font-size: 10px; color: #fde047;">·</td><td class="summary-cell">—</td></tr><tr><td class="sticky-col-3" style="color: #4ade80;">Заработок</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td style="font-size: 11px; color: #4ade80;">·</td><td class="summary-cell" style="color: #4ade80;">0 ₽</td></tr></tbody></table>
        </div>
      </div>
    </div>

    <!-- ВКЛАДКА 4: АДМИНКА -->
    <div id="tab-rates" class="tab-content">
      <div class="card">
        <div style="display: flex; justify-content: space-between; align-items: flex-start; margin-bottom: 16px; border-bottom: 1px solid var(--border-color); padding-bottom: 12px; flex-wrap: wrap; gap: 8px;">
          <div>
            <div class="card-title" style="margin-bottom: 2px;">Админка: Управление &amp; Доступ</div>
            <div style="font-size: 12px; color: var(--text-muted);">
              Исполнители оформлены как <b>самозанятые</b>. Ссылки выдаются ответственным лицам на объекте.
            </div>
          </div>
          <div style="display: flex; gap: 8px; flex-wrap: wrap;">
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #334155;" onclick="exportFullJsonBackup()">💾 Скачать базу</button>
            <input type="file" id="jsonBackupInput" accept=".json" style="display: none;" onchange="importFullJsonBackup(event)">
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #334155;" onclick="document.getElementById('jsonBackupInput').click()">📂 Загрузить базу</button>
          </div>
        </div>

        <!-- БЛОК 1: ОТВЕТСТВЕННЫЕ ЛИЦА И ОБЛАКО -->
        <div style="background: rgba(15, 23, 42, 0.6); border: 1px solid #334155; border-radius: var(--radius-md); padding: 14px; margin-bottom: 20px;">
          
          <div style="background: #0f172a; border: 1px solid #3b82f6; border-radius: var(--radius-sm); padding: 12px; margin-bottom: 16px;">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 6px;">
              <div style="font-size: 12px; font-weight: 700; color: #38bdf8; text-transform: uppercase;">
                ☁️ Статус онлайн-синхронизации (Firebase)
              </div>
              <div style="display: flex; gap: 6px;">
                <button class="action-btn" style="width: auto; padding: 4px 10px; font-size: 11px; background: #2563eb; color: #fff;" onclick="openHostingHelpModal()">📱 Как открыть на телефоне</button>
                <button class="action-btn" style="width: auto; padding: 3px 10px; font-size: 11px; background: #1e293b;" onclick="checkCloudConnectionNow()">🔄 Тест связи</button>
              </div>
            </div>
            
            <div id="cloudDiagnosticMessage" style="font-size: 11px; padding: 8px; border-radius: 4px; margin-bottom: 8px; background: rgba(30, 41, 59, 0.7); color: #cbd5e1; border: 1px solid #334155;">Статус: Облако онлайн</div>

            <div style="display: flex; gap: 6px;">
              <input type="text" id="firebaseDbUrlInput" class="custom-input" placeholder="https://activity-hub-70242-default-rtdb.firebaseio.com" style="font-size: 12px; font-family: monospace;">
              <button class="action-btn btn-start" style="width: auto; padding: 6px 16px; font-size: 12px;" onclick="saveCloudDbUrl()">Сохранить URL</button>
            </div>
          </div>

          <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px;">
            <div style="font-size: 13px; font-weight: 700; color: #38bdf8; text-transform: uppercase;">
              + Добавить нового ответственного (бригадира / куратора объекта)
            </div>
            <span style="font-size: 11px; color: var(--text-muted);">Получает персональную ссылку на пульт</span>
          </div>
          
          <div style="display: grid; grid-template-columns: 2fr 1.5fr 1.5fr 1.5fr 1fr 1fr auto; gap: 8px; margin-bottom: 12px;" class="foreman-add-grid">
            <input type="text" id="newForemanName" class="custom-input" placeholder="ФИО ответственного">
            <input type="text" id="newForemanRole" class="custom-input" placeholder="Должность / Профессия" value="Бригадир">
            <input type="tel" id="newForemanPhone" class="custom-input" placeholder="Телефон / Номер">
            <input type="text" id="newForemanObj" class="custom-input" placeholder="Закрепленный объект">
            <input type="number" id="newForemanRate" class="custom-input" placeholder="Ставка, ₽/ч" value="750">
            <input type="time" id="newForemanStartTime" class="custom-input" title="Время начала работы" value="08:00">
            <button class="action-btn btn-start" style="padding: 9px 16px; font-size: 13px; width: auto;" onclick="addNewForeman()">+ Добавить</button>
          </div>

          <div id="foremenRegistryList" style="display: flex; flex-direction: column; gap: 8px;"><div style="background: rgb(15, 23, 42); border: 1px solid var(--border-color); border-radius: var(--radius-sm); padding: 10px 12px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 8px;">
          <div>
            <div style="display: flex; align-items: center; gap: 6px; flex-wrap: wrap;">
              <span style="font-weight: 700; color: #38bdf8; font-size: 14px;">Дмитрий</span>
              <span style="font-size: 11px; padding: 2px 7px; border-radius: 4px; background: #f59e0b; color: #000; font-weight: 800;">Оператор ЭП</span>
            </div>
            <div style="font-size: 12px; color: var(--text-muted); margin-top: 3px;">
              Телефон: — | Объект: — | Старт: 08:00 | Старт работы: 11.2026
            </div>
            <div style="margin-top: 4px; display: flex; align-items: center; gap: 6px;">
              <span style="font-size: 12px; color: #cbd5e1;">Ставка:</span>
              <input type="number" value="850" style="width: 80px; padding: 2px 6px; font-size: 12px;" class="custom-input" onchange="updateForemanRate(1793895782377, this.value)">
              <span style="font-size: 12px; color: var(--text-muted);">₽/ч</span>
            </div>
          </div>
          <div style="display: flex; gap: 6px; align-items: center; flex-wrap: wrap;">
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #0284c7; color: #fff;" onclick="showForemanQrCode(1793895782377)" title="Показать QR-код для сканирования камерой телефона">📲 QR-код</button>
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #3b82f6; color: #fff;" onclick="openEditForemanModal(1793895782377)" title="Редактировать">✏️</button>
            <button class="action-btn" style="width: auto; padding: 6px 12px; font-size: 12px; background: #2563eb; color: #fff;" onclick="copyPersonalLink('https://05g7uqqedczs95tqnifytadjr2tqzav792taet3n967su94gug-h1008167276.scf.usercontent.googhttps://05g7uqqedczs95tqnifytadjr2tqzav792taet3n967su94gug-h1008167276.scf.usercontent.goog/705ef73d-78ba-4338-a95b-01907dad1a2f/?foreman=1793895782377')">📋 Скопировать ссылку</button>
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #dc2626; color: #fff;" onclick="deleteForeman(1793895782377)">🗑️</button>
          </div>
        </div><div style="background: rgb(15, 23, 42); border: 1px solid var(--border-color); border-radius: var(--radius-sm); padding: 10px 12px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 8px;">
          <div>
            <div style="display: flex; align-items: center; gap: 6px; flex-wrap: wrap;">
              <span style="font-weight: 700; color: #38bdf8; font-size: 14px;">Роман</span>
              <span style="font-size: 11px; padding: 2px 7px; border-radius: 4px; background: #ef4444; color: #fff; font-weight: 800;">Оператор ГНБ</span>
            </div>
            <div style="font-size: 12px; color: var(--text-muted); margin-top: 3px;">
              Телефон: — | Объект: — | Старт: 08:00 | Старт работы: 11.2026
            </div>
            <div style="margin-top: 4px; display: flex; align-items: center; gap: 6px;">
              <span style="font-size: 12px; color: #cbd5e1;">Ставка:</span>
              <input type="number" value="800" style="width: 80px; padding: 2px 6px; font-size: 12px;" class="custom-input" onchange="updateForemanRate(1793895796577, this.value)">
              <span style="font-size: 12px; color: var(--text-muted);">₽/ч</span>
            </div>
          </div>
          <div style="display: flex; gap: 6px; align-items: center; flex-wrap: wrap;">
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #0284c7; color: #fff;" onclick="showForemanQrCode(1793895796577)" title="Показать QR-код для сканирования камерой телефона">📲 QR-код</button>
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #3b82f6; color: #fff;" onclick="openEditForemanModal(1793895796577)" title="Редактировать">✏️</button>
            <button class="action-btn" style="width: auto; padding: 6px 12px; font-size: 12px; background: #2563eb; color: #fff;" onclick="copyPersonalLink('https://05g7uqqedczs95tqnifytadjr2tqzav792taet3n967su94gug-h1008167276.scf.usercontent.googhttps://05g7uqqedczs95tqnifytadjr2tqzav792taet3n967su94gug-h1008167276.scf.usercontent.goog/705ef73d-78ba-4338-a95b-01907dad1a2f/?foreman=1793895796577')">📋 Скопировать ссылку</button>
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #dc2626; color: #fff;" onclick="deleteForeman(1793895796577)">🗑️</button>
          </div>
        </div><div style="background: rgb(15, 23, 42); border: 1px solid var(--border-color); border-radius: var(--radius-sm); padding: 10px 12px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 8px;">
          <div>
            <div style="display: flex; align-items: center; gap: 6px; flex-wrap: wrap;">
              <span style="font-weight: 700; color: #38bdf8; font-size: 14px;">Маршит</span>
              <span style="font-size: 11px; padding: 2px 7px; border-radius: 4px; background: #f59e0b; color: #000; font-weight: 800;">Оператор ЭП</span>
            </div>
            <div style="font-size: 12px; color: var(--text-muted); margin-top: 3px;">
              Телефон: — | Объект: — | Старт: 08:00 | Старт работы: 11.2026
            </div>
            <div style="margin-top: 4px; display: flex; align-items: center; gap: 6px;">
              <span style="font-size: 12px; color: #cbd5e1;">Ставка:</span>
              <input type="number" value="750" style="width: 80px; padding: 2px 6px; font-size: 12px;" class="custom-input" onchange="updateForemanRate(1793895806521, this.value)">
              <span style="font-size: 12px; color: var(--text-muted);">₽/ч</span>
            </div>
          </div>
          <div style="display: flex; gap: 6px; align-items: center; flex-wrap: wrap;">
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #0284c7; color: #fff;" onclick="showForemanQrCode(1793895806521)" title="Показать QR-код для сканирования камерой телефона">📲 QR-код</button>
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #3b82f6; color: #fff;" onclick="openEditForemanModal(1793895806521)" title="Редактировать">✏️</button>
            <button class="action-btn" style="width: auto; padding: 6px 12px; font-size: 12px; background: #2563eb; color: #fff;" onclick="copyPersonalLink('https://05g7uqqedczs95tqnifytadjr2tqzav792taet3n967su94gug-h1008167276.scf.usercontent.googhttps://05g7uqqedczs95tqnifytadjr2tqzav792taet3n967su94gug-h1008167276.scf.usercontent.goog/705ef73d-78ba-4338-a95b-01907dad1a2f/?foreman=1793895806521')">📋 Скопировать ссылку</button>
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #dc2626; color: #fff;" onclick="deleteForeman(1793895806521)">🗑️</button>
          </div>
        </div><div style="background: rgb(15, 23, 42); border: 1px solid var(--border-color); border-radius: var(--radius-sm); padding: 10px 12px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 8px;">
          <div>
            <div style="display: flex; align-items: center; gap: 6px; flex-wrap: wrap;">
              <span style="font-weight: 700; color: #38bdf8; font-size: 14px;">Николай</span>
              <span style="font-size: 11px; padding: 2px 7px; border-radius: 4px; background: #f59e0b; color: #000; font-weight: 800;">Оператор ЭП</span>
            </div>
            <div style="font-size: 12px; color: var(--text-muted); margin-top: 3px;">
              Телефон: — | Объект: — | Старт: 08:00 | Старт работы: 11.2026
            </div>
            <div style="margin-top: 4px; display: flex; align-items: center; gap: 6px;">
              <span style="font-size: 12px; color: #cbd5e1;">Ставка:</span>
              <input type="number" value="750" style="width: 80px; padding: 2px 6px; font-size: 12px;" class="custom-input" onchange="updateForemanRate(1793895829681, this.value)">
              <span style="font-size: 12px; color: var(--text-muted);">₽/ч</span>
            </div>
          </div>
          <div style="display: flex; gap: 6px; align-items: center; flex-wrap: wrap;">
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #0284c7; color: #fff;" onclick="showForemanQrCode(1793895829681)" title="Показать QR-код для сканирования камерой телефона">📲 QR-код</button>
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #3b82f6; color: #fff;" onclick="openEditForemanModal(1793895829681)" title="Редактировать">✏️</button>
            <button class="action-btn" style="width: auto; padding: 6px 12px; font-size: 12px; background: #2563eb; color: #fff;" onclick="copyPersonalLink('https://05g7uqqedczs95tqnifytadjr2tqzav792taet3n967su94gug-h1008167276.scf.usercontent.googhttps://05g7uqqedczs95tqnifytadjr2tqzav792taet3n967su94gug-h1008167276.scf.usercontent.goog/705ef73d-78ba-4338-a95b-01907dad1a2f/?foreman=1793895829681')">📋 Скопировать ссылку</button>
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #dc2626; color: #fff;" onclick="deleteForeman(1793895829681)">🗑️</button>
          </div>
        </div><div style="background: rgb(15, 23, 42); border: 1px solid var(--border-color); border-radius: var(--radius-sm); padding: 10px 12px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 8px;">
          <div>
            <div style="display: flex; align-items: center; gap: 6px; flex-wrap: wrap;">
              <span style="font-weight: 700; color: #38bdf8; font-size: 14px;">Гномыч</span>
              <span style="font-size: 11px; padding: 2px 7px; border-radius: 4px; background: #22c55e; color: #000; font-weight: 800;">Слесарь</span>
            </div>
            <div style="font-size: 12px; color: var(--text-muted); margin-top: 3px;">
              Телефон: — | Объект: Сухарка | Старт: 08:00 | Старт работы: 11.2026
            </div>
            <div style="margin-top: 4px; display: flex; align-items: center; gap: 6px;">
              <span style="font-size: 12px; color: #cbd5e1;">Ставка:</span>
              <input type="number" value="500" style="width: 80px; padding: 2px 6px; font-size: 12px;" class="custom-input" onchange="updateForemanRate(1793959015828, this.value)">
              <span style="font-size: 12px; color: var(--text-muted);">₽/ч</span>
            </div>
          </div>
          <div style="display: flex; gap: 6px; align-items: center; flex-wrap: wrap;">
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #0284c7; color: #fff;" onclick="showForemanQrCode(1793959015828)" title="Показать QR-код для сканирования камерой телефона">📲 QR-код</button>
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #3b82f6; color: #fff;" onclick="openEditForemanModal(1793959015828)" title="Редактировать">✏️</button>
            <button class="action-btn" style="width: auto; padding: 6px 12px; font-size: 12px; background: #2563eb; color: #fff;" onclick="copyPersonalLink('https://05g7uqqedczs95tqnifytadjr2tqzav792taet3n967su94gug-h1008167276.scf.usercontent.googhttps://05g7uqqedczs95tqnifytadjr2tqzav792taet3n967su94gug-h1008167276.scf.usercontent.goog/705ef73d-78ba-4338-a95b-01907dad1a2f/?foreman=1793959015828')">📋 Скопировать ссылку</button>
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #dc2626; color: #fff;" onclick="deleteForeman(1793959015828)">🗑️</button>
          </div>
        </div></div>
        </div>

        <!-- БЛОК 2: САМОЗАНЯТЫЕ И СТАВКИ -->
        <div style="background: rgba(15, 23, 42, 0.4); border: 1px solid var(--border-color); border-radius: var(--radius-md); padding: 14px;">
          <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; flex-wrap: wrap; gap: 8px;">
            <div style="display: flex; align-items: center; gap: 10px;">
              <div style="font-size: 13px; font-weight: 700; color: #cbd5e1; text-transform: uppercase;">
                👷 Самозанятые исполнители (все добавленные на объектах)
              </div>
              <span id="employeesCountBadge" style="font-size: 11px; background: #334155; color: #38bdf8; padding: 2px 8px; border-radius: 12px; font-weight: 700;">Всего: 0</span>
            </div>
            <div style="display: flex; gap: 8px; align-items: center;">
              <input type="text" id="adminEmployeeSearchInput" class="custom-input" placeholder="🔍 Быстрый поиск по реестру..." style="font-size: 12px; padding: 5px 10px; width: 220px;" oninput="renderRatesTable()">
              <div style="font-size: 11px; background: rgba(59, 130, 246, 0.15); color: #93c5fd; padding: 2px 8px; border-radius: 4px; border: 1px solid #1d4ed8;">
                Статус: Самозанятость (ГПХ)
              </div>
            </div>
          </div>

          <div style="display: grid; grid-template-columns: 2fr 1.5fr 1.5fr 1fr auto; gap: 8px; margin-bottom: 12px;" class="foreman-add-grid">
            <input type="text" id="newEmpName" class="custom-input" placeholder="ФИО самозанятого">
            <input type="text" id="newEmpRole" class="custom-input" placeholder="Специализация / Роль">
            <input type="tel" id="newEmpPhone" class="custom-input" placeholder="Телефон / Номер">
            <input type="number" id="newEmpRate" class="custom-input" placeholder="Ставка, ₽/ч" value="500" title="4000 ₽ за 8 часов (+ 1 час обед)">
            <button class="action-btn btn-start" style="padding: 9px 16px; font-size: 13px; width: auto;" onclick="addNewEmployee()">+ В реестр</button>
          </div>

          <div style="font-size: 11px; color: #94a3b8; margin-bottom: 8px;">
            💡 <b>Стандартная смена самозанятого:</b> 4 000 ₽ за 8 рабочих часов + 1 час обеда (ставка 500 ₽/ч; при смене от 8 часов 1 час обеда вычитается автоматически).
          </div>

          <div class="table-responsive">
            <table class="matrix-table" style="font-size: 13px;">
              <thead>
                <tr>
                  <th style="width: 45px;">№</th>
                  <th style="text-align: left;">ФИО самозанятого</th>
                  <th>Специализация</th>
                  <th>Номер телефона</th>
                  <th style="width: 130px;">Ставка (₽/час)</th>
                  <th style="width: 120px;">Старт работы</th>
                  <th style="width: 120px;">Видимость</th>
                  <th style="width: 110px;">Действия</th>
                </tr>
              </thead>
              <tbody id="employeesRatesTableBody"><tr><td colspan="8" style="padding: 16px; color: var(--text-muted);">Самозанятые не найдены</td></tr></tbody>
            </table>
          </div>
        </div>

        <!-- БЛОК 3: АРХИВ СОТРУДНИКОВ -->
        <div style="background: rgba(15, 23, 42, 0.4); border: 1px solid #475569; border-radius: var(--radius-md); padding: 14px; margin-top: 20px;">
          <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; flex-wrap: wrap; gap: 8px;">
            <div style="display: flex; align-items: center; gap: 10px;">
              <div style="font-size: 13px; font-weight: 700; color: #cbd5e1; text-transform: uppercase;">
                📦 Архив сотрудников (сохранённые данные)
              </div>
              <span id="archivedCountBadge" style="font-size: 11px; background: #334155; color: #94a3b8; padding: 2px 8px; border-radius: 12px; font-weight: 700;">В архиве: 0</span>
            </div>
            <div style="font-size: 11px; color: #94a3b8;">
              Сотрудники не удаляются безвозвратно. Их можно восстановить в любой момент.
            </div>
          </div>

          <div class="table-responsive">
            <table class="matrix-table" style="font-size: 13px;">
              <thead>
                <tr>
                  <th style="width: 45px;">№</th>
                  <th style="text-align: left;">ФИО</th>
                  <th>Роль / Профессия</th>
                  <th>Категория</th>
                  <th>Телефон</th>
                  <th>Ставка</th>
                  <th>Дата архивации</th>
                  <th style="width: 130px;">Действие</th>
                </tr>
              </thead>
              <tbody id="archivedEmployeesTableBody"><tr><td colspan="8" style="padding: 16px; color: var(--text-muted);">Архив пуст</td></tr></tbody>
            </table>
          </div>
        </div>

      </div>
    </div>

  </div>

  <!-- МОДАЛЬНОЕ ОКНО: РЕДАКТИРОВАНИЕ САМОЗАНЯТОГО -->
  <div class="modal-overlay" id="editEmployeeModal">
    <div class="modal-box">
      <div class="modal-title" style="color: #38bdf8;">✏️ Редактирование карточки самозанятого</div>
      <input type="hidden" id="editEmpIdInput">

      <div>
        <label style="font-size: 12px; color: var(--text-muted);">ФИО самозанятого:</label>
        <input type="text" id="editEmpNameInput" class="custom-input" style="margin-top: 4px;">
      </div>

      <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 8px;">
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Специализация / Должность:</label>
          <input type="text" id="editEmpRoleInput" class="custom-input" style="margin-top: 4px;">
        </div>
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Телефон / Номер:</label>
          <input type="tel" id="editEmpPhoneInput" class="custom-input" style="margin-top: 4px;">
        </div>
      </div>

      <div style="display: grid; grid-template-columns: 1fr 1fr 1fr; gap: 8px;">
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Ставка (₽/час):</label>
          <input type="number" id="editEmpRateInput" class="custom-input" style="margin-top: 4px;">
        </div>
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Месяц старта:</label>
          <input type="number" min="1" max="12" id="editEmpStartMonthInput" class="custom-input" style="margin-top: 4px;">
        </div>
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Год старта:</label>
          <input type="number" min="2024" max="2035" id="editEmpStartYearInput" class="custom-input" style="margin-top: 4px;">
        </div>
      </div>

      <div style="display: flex; gap: 8px; margin-top: 8px;">
        <button class="action-btn btn-start" style="padding: 10px; font-size: 13px;" onclick="saveEmployeeCardEdit()">Сохранить изменения</button>
        <button class="action-btn" style="padding: 10px; font-size: 13px; background: #475569; color: #fff; width: auto;" onclick="closeEmployeeEditModal()">Отмена</button>
      </div>
    </div>
  </div>

  <!-- МОДАЛЬНОЕ ОКНО: РЕДАКТИРОВАНИЕ ОТВЕТСТВЕННОГО -->
  <div class="modal-overlay" id="editForemanModal">
    <div class="modal-box">
      <div class="modal-title" style="color: #38bdf8;">✏️ Редактирование карточки ответственного</div>
      <input type="hidden" id="editForemanIdInput">

      <div>
        <label style="font-size: 12px; color: var(--text-muted);">ФИО ответственного:</label>
        <input type="text" id="editForemanNameInput" class="custom-input" style="margin-top: 4px;">
      </div>

      <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 8px;">
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Должность / Профессия:</label>
          <input type="text" id="editForemanRoleInput" class="custom-input" style="margin-top: 4px;">
        </div>
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Телефон / Номер:</label>
          <input type="tel" id="editForemanPhoneInput" class="custom-input" style="margin-top: 4px;">
        </div>
      </div>

      <div style="display: grid; grid-template-columns: 1.5fr 1fr 1fr; gap: 8px;">
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Закреплённый объект:</label>
          <input type="text" id="editForemanObjInput" class="custom-input" style="margin-top: 4px;">
        </div>
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Ставка (₽/час):</label>
          <input type="number" id="editForemanRateInput" class="custom-input" style="margin-top: 4px;">
        </div>
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Время старта:</label>
          <input type="time" id="editForemanStartTimeInput" class="custom-input" style="margin-top: 4px;">
        </div>
      </div>

      <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 8px;">
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Месяц старта:</label>
          <input type="number" min="1" max="12" id="editForemanStartMonthInput" class="custom-input" style="margin-top: 4px;">
        </div>
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Год старта:</label>
          <input type="number" min="2024" max="2035" id="editForemanStartYearInput" class="custom-input" style="margin-top: 4px;">
        </div>
      </div>

      <div style="display: flex; gap: 8px; margin-top: 8px;">
        <button class="action-btn btn-start" style="padding: 10px; font-size: 13px;" onclick="saveForemanCardEdit()">Сохранить изменения</button>
        <button class="action-btn" style="padding: 10px; font-size: 13px; background: #475569; color: #fff; width: auto;" onclick="closeForemanEditModal()">Отмена</button>
      </div>
    </div>
  </div>

  <!-- МОДАЛЬНОЕ ОКНО: «Я ОШИБСЯ» -->
  <div class="modal-overlay" id="mistakeModal">
    <div class="modal-box">
      <div class="modal-title" style="color: #fde047;">⚠️ Внести уточнение (Я ошибся)</div>
      <div style="font-size: 12px; color: var(--text-muted);">
        Первичные факт-отметки и координаты останутся в архиве для проверки, а администратор увидит ваше уточнение в отдельной графе табеля.
      </div>

      <div>
        <label style="font-size: 12px; color: var(--text-muted);">Самозанятый, по которому возникла ошибка:</label>
        <select id="mistakeWorkerSelect" class="custom-select" style="width: 100%; margin-top: 4px; padding: 10px;"></select>
      </div>

      <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 8px;">
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Правильный старт:</label>
          <input type="time" id="mistakeStartInput" class="custom-input" style="width: 100%; margin-top: 4px;">
        </div>
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Правильный финиш:</label>
          <input type="time" id="mistakeEndInput" class="custom-input" style="width: 100%; margin-top: 4px;">
        </div>
      </div>

      <div>
        <label style="font-size: 12px; color: var(--text-muted);">Правильный объект:</label>
        <input type="text" id="mistakeObjectInput" class="custom-input" placeholder="Название объекта" style="width: 100%; margin-top: 4px;">
      </div>

      <div>
        <label style="font-size: 12px; color: #fde047; font-weight: 600;">Что произошло / Причина ошибки:</label>
        <input type="text" id="mistakeReasonInput" class="custom-input" placeholder="Например: случайно нажал кнопку, работал с 08:00" style="width: 100%; margin-top: 4px; border-color: #f59e0b;">
      </div>

      <div style="display: flex; gap: 8px; margin-top: 8px;">
        <button class="action-btn btn-start" style="padding: 12px; font-size: 14px; background: #d97706;" onclick="submitMistakeCorrection()">Отправить уточнение</button>
        <button class="action-btn btn-stop" style="padding: 12px; font-size: 14px; background: #475569;" onclick="closeMistakeModal()">Отмена</button>
      </div>
    </div>
  </div>

  <!-- МОДАЛЬНОЕ ОКНО: РЕДАКТИРОВАНИЕ ДНЯ В ТАБЕЛЕ (АДМИН) -->
  <div class="modal-overlay" id="editModal">
    <div class="modal-box">
      <div class="modal-title" id="editModalTitle">Редактирование смены</div>
      
      <div>
        <label style="font-size: 12px; color: var(--text-muted);">Объект:</label>
        <input type="text" id="modalObject" class="custom-input" style="margin-top: 4px;">
      </div>

      <div style="display: grid; grid-template-columns: 1fr 1fr; gap: 8px;">
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Начало смены:</label>
          <input type="time" id="modalStart" class="custom-input" style="margin-top: 4px;">
        </div>
        <div>
          <label style="font-size: 12px; color: var(--text-muted);">Конец смены:</label>
          <input type="time" id="modalEnd" class="custom-input" style="margin-top: 4px;">
        </div>
      </div>

      <div style="background: #0f172a; border: 1px solid var(--border-color); border-radius: var(--radius-sm); padding: 10px; font-size: 12px;" id="modalAuditBlock"></div>

      <div style="display: flex; gap: 8px; margin-top: 6px;">
        <button class="action-btn btn-start" style="padding: 10px; font-size: 13px;" onclick="saveModalEdit()">Сохранить</button>
        <button class="action-btn" style="padding: 10px; font-size: 13px; background: #dc2626; color: #fff; width: auto;" onclick="deleteModalShift()">Удалить смену</button>
        <button class="action-btn" style="padding: 10px; font-size: 13px; background: #334155; color: #fff; width: auto;" onclick="closeEditModal()">Закрыть</button>
      </div>
    </div>
  </div>

  <!-- МОДАЛЬНОЕ ОКНО: ПРОСМОТР ФОТО -->
  <div class="modal-overlay" id="photoViewModal" onclick="closePhotoViewModal()">
    <div style="max-width: 90vw; max-height: 90vh; display: flex; flex-direction: column; align-items: center; gap: 10px;">
      <img id="photoViewImg" src="" style="max-width: 100%; max-height: 80vh; border-radius: var(--radius-md); border: 2px solid #334155;">
      <button class="action-btn" style="width: auto; padding: 6px 16px; background: #dc2626; color: #fff;" onclick="closePhotoViewModal()">Закрыть</button>
    </div>
  </div>

  <!-- МОДАЛЬНОЕ ОКНО: ПОДСКАЗКА ПО ХОСТИНГУ ДЛЯ ТЕЛЕФОНА -->
  <div class="modal-overlay" id="hostingHelpModal">
    <div class="modal-box" style="max-width: 550px;">
      <div class="modal-title" style="color: #38bdf8; display: flex; align-items: center; gap: 8px;">
        <span>🌐</span> Как открыть пульт на смартфонах
      </div>

      <div style="font-size: 13px; color: #cbd5e1; line-height: 1.5;">
        Чтобы ссылка открывалась на телефонах ответственных в любой точке города, файлу нужен настоящий веб-адрес в интернете:
      </div>

      <div style="background: #0f172a; border: 1px solid #334155; border-radius: 8px; padding: 12px; font-size: 12px; color: #e2e8f0; display: flex; flex-direction: column; gap: 8px;">
        <div><b>Шаг 1:</b> Нажмите зеленую кнопку вверху справа <b>«💾 Скачать index.html»</b>.</div>
        <div><b>Шаг 2:</b> Опубликуйте на Vercel или перетащите файл на сайт <a href="https://app.netlify.com/drop" target="_blank" style="color: #38bdf8; font-weight: 700; text-decoration: underline;" rel="noopener noreferrer">app.netlify.com/drop</a>.</div>
        <div><b>Шаг 3:</b> Вы сразу получите рабочий веб-адрес.</div>
      </div>

      <div style="margin-top: 4px;">
        <label style="font-size: 12px; font-weight: 700; color: #fde047;">Вставьте сюда полученный адрес с хостинга:</label>
        <div style="display: flex; gap: 6px; margin-top: 4px;">
          <input type="text" id="customPublicDomainInput" class="custom-input" placeholder="https://uchet-smen-tabel.vercel.app" style="font-size: 13px;">
          <button class="action-btn btn-start" style="width: auto; padding: 8px 14px; font-size: 12px;" onclick="saveCustomPublicDomain()">Применить</button>
        </div>
      </div>

      <div style="display: flex; justify-content: flex-end; margin-top: 6px;">
        <button class="action-btn" style="width: auto; padding: 8px 16px; background: #475569; color: #fff;" onclick="closeHostingHelpModal()">Понятно / Закрыть</button>
      </div>
    </div>
  </div>

  <!-- МОДАЛЬНОЕ ОКНО: QR-КОД -->
  <div class="modal-overlay" id="qrCodeModal">
    <div class="modal-box" style="max-width: 380px; text-align: center; align-items: center;">
      <div class="modal-title" id="qrModalTitle" style="color: #38bdf8; font-size: 15px;">Вход для ответственного</div>
      <div style="font-size: 12px; color: var(--text-muted); margin-bottom: 8px;" id="qrModalSubtitle">Наведите камеру смартфона на экран</div>
      
      <div id="qrCodeContainer" style="background: #ffffff; padding: 12px; border-radius: 12px; display: inline-block; box-shadow: 0 4px 16px rgba(0,0,0,0.4);">
        <img id="qrCodeImage" src="" alt="QR Code" style="width: 220px; height: 220px; display: block;">
      </div>

      <div style="font-size: 11px; color: #94a3b8; word-break: break-all; margin-top: 6px; max-width: 100%;" id="qrModalUrlText"></div>

      <div style="display: flex; gap: 8px; width: 100%; margin-top: 8px;">
        <button class="action-btn btn-start" style="padding: 9px; font-size: 12px;" onclick="copyQrLinkFromModal()">Скопировать ссылку</button>
        <button class="action-btn" style="padding: 9px; font-size: 12px; background: #475569; color: #fff; width: auto;" onclick="closeQrModal()">Закрыть</button>
      </div>
    </div>
  </div>

  <!-- МОДАЛЬНОЕ ОКНО: БЫСТРЫЙ ВЫБОР ОТВЕТСТВЕННОГО ПРЯМО НА ТЕЛЕФОНЕ (БЕЗ ССЫЛОК) -->
  <div class="modal-overlay" id="switchForemanModal">
    <div class="modal-box" style="max-width: 380px;">
      <div class="modal-title" style="color: #38bdf8;">👷‍♂️ Выберите ваш профиль</div>
      <div style="font-size: 12px; color: var(--text-muted);">
        Выберите ваше имя, чтобы открыть персональный пульт на этом телефоне:
      </div>
      <div id="switchForemanModalList" style="display: flex; flex-direction: column; gap: 8px; margin-top: 6px; max-height: 300px; overflow-y: auto;"></div>
      <div style="display: flex; justify-content: flex-end; margin-top: 8px;">
        <button class="action-btn" style="width: auto; padding: 8px 16px; background: #475569; color: #fff;" onclick="closeSwitchForemanModal()">Закрыть</button>
      </div>
    </div>
  </div>

  <!-- ВСПЛЫВАЮЩЕЕ УВЕДОМЛЕНИЕ -->
  <div id="toastMessage"></div>

  <script>
    /* ==============================================================
       СОСТОЯНИЕ И БАЗОВЫЕ ДАННЫЕ
       ============================================================== */
    let firebaseDbUrl = "https://activity-hub-70242-default-rtdb.firebaseio.com";
    let cloudSyncInterval = null;
    let isCloudSyncing = false;

    let employees = [];

    let foremenList = [
      { id: 1793895782377, name: "Дмитрий", role: "Оператор ЭП", phone: "", defaultObject: "Сухарка", rate: 850, startTime: "08:00", startMonth: 11, startYear: 2026 },
      { id: 1793895796577, name: "Роман", role: "Оператор ГНБ", phone: "", defaultObject: "Сухарка", rate: 800, startTime: "08:00", startMonth: 11, startYear: 2026 },
      { id: 1793895806521, name: "Маршит", role: "Оператор ЭП", phone: "", defaultObject: "Сухарка", rate: 750, startTime: "08:00", startMonth: 11, startYear: 2026 },
      { id: 1793895829681, name: "Николай", role: "Оператор ЭП", phone: "", defaultObject: "Сухарка", rate: 750, startTime: "08:00", startMonth: 11, startYear: 2026 },
      { id: 1793959015828, name: "Гномыч", role: "Слесарь", phone: "", defaultObject: "Сухарка", rate: 500, startTime: "08:00", startMonth: 11, startYear: 2026 }
    ];

    let archivedWorkers = [];
    let objectsList = ["Сухарка"];
    let selectedObject = "Сухарка";
    let shiftsDb = {};
    let universalDocs = [];

    let currentForemanUser = null;
    let shiftMode = "start"; // "start" | "stop"
    let selectedWorkerIds = new Set();
    let currentGpsCoords = null;
    let publicHostingDomain = "https://uchet-smen-tabel.vercel.app";
    let activeQrLink = "";

    let currentYear = 2026;
    let currentMonth = 11;
    let editingShiftContext = null;
    let deferredPwaPrompt = null;

    /* ==============================================================
       PWA ИНСТАЛЛЯТОР И ПОДДЕРЖКА ДЛЯ ANDROID
       ============================================================== */
    function initPwaSupport() {
      try {
        window.addEventListener("beforeinstallprompt", (e) => {
          e.preventDefault();
          deferredPwaPrompt = e;
          const box = document.getElementById("pwaInstallPromptBox");
          if (box) box.style.display = "flex";
        });
      } catch (e) {}
    }

    function triggerPwaInstall() {
      if (deferredPwaPrompt) {
        deferredPwaPrompt.prompt();
        deferredPwaPrompt.userChoice.then((choice) => {
          if (choice.outcome === "accepted") {
            showToast("Приложение устанавливается на рабочий стол!");
          }
          deferredPwaPrompt = null;
          const box = document.getElementById("pwaInstallPromptBox");
          if (box) box.style.display = "none";
        });
      } else {
        showToast("Нажмите в браузере ⋮ (три точки) -> «Добавить на гл. экран»");
      }
    }

    function openSwitchForemanModal() {
      const container = document.getElementById("switchForemanModalList");
      if (!container) return;
      container.innerHTML = "";

      foremenList.forEach(f => {
        const btn = document.createElement("button");
        btn.className = "action-btn";
        btn.style = "background: #1e293b; border: 1px solid #334155; padding: 10px 14px; text-align: left; justify-content: space-between; font-size: 13px; color: #f8fafc;";
        const isCurrent = currentForemanUser && currentForemanUser.id === f.id;
        btn.innerHTML = `
          <span><b>${f.name}</b> <span style="font-size: 11px; color: #94a3b8;">(${f.role})</span></span>
          <span style="color: ${isCurrent ? '#38bdf8' : '#64748b'}; font-weight: 700;">${isCurrent ? '● Активен' : 'Выбрать'}</span>
        `;
        btn.onclick = () => {
          selectForemanProfileDirectly(f.id);
          closeSwitchForemanModal();
        };
        container.appendChild(btn);
      });

      document.getElementById("switchForemanModal").classList.add("open");
    }

    function closeSwitchForemanModal() {
      const m = document.getElementById("switchForemanModal");
      if (m) m.classList.remove("open");
    }

    function selectForemanProfileDirectly(foremanId) {
      const found = foremenList.find(f => f.id === foremanId);
      if (!found) return;
      currentForemanUser = found;
      safeSetItem("ah_saved_device_foreman_id", String(found.id));
      const nameDisp = document.getElementById("currentForemanDisplay");
      if (nameDisp) nameDisp.innerText = currentForemanUser.name;
      if (currentForemanUser.defaultObject) {
        selectedObject = currentForemanUser.defaultObject;
      }
      renderForemanWorkers();
      showToast(`Профиль активирован: ${found.name}`);
    }

    /* ==============================================================
       УВЕДОМЛЕНИЯ (ТОСТЫ)
       ============================================================== */
    function showToast(text, duration = 3000) {
      try {
        const toast = document.getElementById("toastMessage");
        if (!toast) return;
        toast.innerText = text;
        toast.style.display = "block";
        clearTimeout(toast._timeout);
        toast._timeout = setTimeout(() => {
          toast.style.display = "none";
        }, duration);
      } catch (e) {
        console.warn("Toast error:", e);
      }
    }

    /* ==============================================================
       СОХРАНЕНИЕ И ЗАГРУЗКА (SAFE-STORAGE ДЛЯ МОБИЛЬНЫХ БРАУЗЕРОВ)
       ============================================================== */
    const memStore = {};
    function safeGetItem(key) {
      try {
        return window.localStorage.getItem(key);
      } catch (e) {
        return memStore[key] || null;
      }
    }
    function safeSetItem(key, val) {
      try {
        window.localStorage.setItem(key, val);
      } catch (e) {
        memStore[key] = String(val);
      }
    }

    function loadState() {
      try {
        const savedFb = safeGetItem("ah_fb_url");
        if (savedFb) firebaseDbUrl = savedFb;

        const savedDomain = safeGetItem("ah_public_domain");
        if (savedDomain) {
          publicHostingDomain = savedDomain;
        } else {
          publicHostingDomain = "https://uchet-smen-tabel.vercel.app";
        }
        const domInp = document.getElementById("customPublicDomainInput");
        if (domInp) domInp.value = publicHostingDomain;

        const fbInput = document.getElementById("firebaseDbUrlInput");
        if (fbInput) fbInput.value = firebaseDbUrl;

        const savedEmps = safeGetItem("ah_employees");
        if (savedEmps) {
          employees = JSON.parse(savedEmps);
          const testNames = ["Иванов Алексей", "Сидоров Дмитрий", "Кузнецов Роман", "Сергеев Михаил"];
          employees = employees.filter(e => !testNames.includes(e.name));
        }

        const savedForemen = safeGetItem("ah_foremen");
        if (savedForemen) {
          const parsedF = JSON.parse(savedForemen);
          if (Array.isArray(parsedF) && parsedF.length > 0) {
            foremenList = parsedF;
          }
        }

        const savedArchive = safeGetItem("ah_archived_workers");
        if (savedArchive) archivedWorkers = JSON.parse(savedArchive);

        const savedObjs = safeGetItem("ah_objects");
        if (savedObjs) {
          const parsedO = JSON.parse(savedObjs);
          if (Array.isArray(parsedO) && parsedO.length > 0) {
            objectsList = parsedO;
          }
        }

        const savedShifts = safeGetItem("ah_shifts");
        if (savedShifts) shiftsDb = JSON.parse(savedShifts);

        const savedDocs = safeGetItem("ah_docs");
        if (savedDocs) universalDocs = JSON.parse(savedDocs);
      } catch (e) {
        console.warn("Ошибка чтения хранилища:", e);
      }
    }

    function saveState() {
      try {
        safeSetItem("ah_fb_url", firebaseDbUrl);
        safeSetItem("ah_public_domain", publicHostingDomain);
        safeSetItem("ah_employees", JSON.stringify(employees));
        safeSetItem("ah_foremen", JSON.stringify(foremenList));
        safeSetItem("ah_archived_workers", JSON.stringify(archivedWorkers));
        safeSetItem("ah_objects", JSON.stringify(objectsList));
        safeSetItem("ah_shifts", JSON.stringify(shiftsDb));
        safeSetItem("ah_docs", JSON.stringify(universalDocs));
      } catch (e) {
        console.warn("Ошибка записи хранилища:", e);
      }
    }

    /* ==============================================================
       ОБЛАЧНАЯ СИНХРОНИЗАЦИЯ FIREBASE (С ПОДДЕРЖКОЙ ССЫЛОК)
       ============================================================== */
    let lastLocalPushTimestamp = 0;

    function updateCloudStatus(status, text, detail = "") {
      try {
        const badge = document.getElementById("cloudStatusIndicator");
        const diag = document.getElementById("cloudDiagnosticMessage");
        if (badge) {
          badge.className = `cloud-status-badge ${status}`;
          badge.innerHTML = `<span class="status-dot">${status === "online" ? "🟢" : "🟡"}</span> ${text}`;
        }
        if (diag) {
          diag.innerText = `Статус: ${text}${detail ? " | " + detail : ""}`;
        }
      } catch (e) {}
    }

    function cleanFirebaseUrl(url) {
      if (!url) return "";
      let u = String(url).trim();
      if (!u.startsWith("http://") && !u.startsWith("https://")) {
        u = "https://" + u;
      }
      return u.replace(/\/+$/, "");
    }

    async function pushStateToCloud() {
      if (!firebaseDbUrl) return;
      const base = cleanFirebaseUrl(firebaseDbUrl);
      lastLocalPushTimestamp = Date.now();
      try {
        const payload = {
          employees,
          foremenList,
          archivedWorkers,
          objectsList,
          shiftsDb,
          universalDocs,
          updatedAt: lastLocalPushTimestamp
        };
        const controller = new AbortController();
        const tid = setTimeout(() => controller.abort(), 2500);
        const res = await fetch(`${base}/hubData.json`, {
          method: "PUT",
          headers: { "Content-Type": "application/json" },
          body: JSON.stringify(payload),
          signal: controller.signal
        });
        clearTimeout(tid);
        if (res.ok) {
          updateCloudStatus("online", "Облако онлайн");
        } else {
          updateCloudStatus("offline", `Код ${res.status}`);
        }
      } catch (err) {
        updateCloudStatus("offline", "Офлайн-режим");
      }
    }

    function applyRemoteData(remote) {
      if (!remote || typeof remote !== "object") return;
      
      const testNames = ["Иванов Алексей", "Сидоров Дмитрий", "Кузнецов Роман", "Сергеев Михаил"];

      if (remote.employees && Array.isArray(remote.employees)) {
        employees = remote.employees.filter(e => !testNames.includes(e.name));
      }
      if (remote.foremenList && Array.isArray(remote.foremenList) && remote.foremenList.length > 0) {
        foremenList = remote.foremenList;
      }
      if (remote.archivedWorkers && Array.isArray(remote.archivedWorkers)) {
        archivedWorkers = remote.archivedWorkers;
      }
      if (remote.objectsList && Array.isArray(remote.objectsList) && remote.objectsList.length > 0) {
        objectsList = remote.objectsList;
      }
      if (remote.shiftsDb && typeof remote.shiftsDb === "object") {
        shiftsDb = remote.shiftsDb;
      }
      if (remote.universalDocs && Array.isArray(remote.universalDocs)) {
        universalDocs = remote.universalDocs;
      }

      saveState();

      // Автоматическая привязка ответственного по ссылке ?foreman=
      checkAndRebindForemanUrl();

      try {
        renderObjectsSelect();
        renderForemanWorkers();
        renderRatesTable();
        renderArchivedWorkersTable();
        renderMatrixTable();
        renderUniversalDocsTable();
        renderForemenRegistry();
      } catch (e) {
        console.warn("Render error after sync:", e);
      }
    }

    function checkAndRebindForemanUrl() {
      try {
        const params = new URLSearchParams(window.location.search || "");
        const fid = params.get("foreman");
        if (fid) {
          const fidStr = String(fid);
          const found = foremenList.find(f => String(f.id) === fidStr);
          if (found && (!currentForemanUser || currentForemanUser.name !== found.name)) {
            currentForemanUser = found;
            const nameDisp = document.getElementById("currentForemanDisplay");
            if (nameDisp) nameDisp.innerText = currentForemanUser.name;
            if (currentForemanUser.defaultObject) {
              selectedObject = currentForemanUser.defaultObject;
            }
            renderForemanWorkers();
          }
        }
      } catch (e) {}
    }

    async function pullStateFromCloud(silent = true) {
      if (!firebaseDbUrl || isCloudSyncing) return;
      const base = cleanFirebaseUrl(firebaseDbUrl);
      isCloudSyncing = true;
      try {
        const controller = new AbortController();
        // Сверхкороткий таймаут 1.5 сек, чтобы телефон никогда не зависал при сбоях оператора
        const timeoutId = setTimeout(() => controller.abort(), 1500);

        const res = await fetch(`${base}/hubData.json`, { signal: controller.signal });
        clearTimeout(timeoutId);

        if (res.ok) {
          const remote = await res.json();
          if (remote) {
            applyRemoteData(remote);
          }
          updateCloudStatus("online", "Облако онлайн");
          const netAlert = document.getElementById("netStatusAlert");
          if (netAlert) netAlert.style.display = "none";
          if (!silent) showToast("Данные синхронизированы!");
        } else {
          updateCloudStatus("offline", "Офлайн");
        }
      } catch (err) {
        updateCloudStatus("offline", "Офлайн");
        // Не крашим интерфейс, работаем полностью автономно
      } finally {
        isCloudSyncing = false;
      }
    }

    function checkCloudConnectionNow() {
      pullStateFromCloud(false);
    }

    function saveCloudDbUrl() {
      const input = document.getElementById("firebaseDbUrlInput");
      if (!input || !input.value.trim()) {
        showToast("Введите URL базы данных Firebase");
        return;
      }
      firebaseDbUrl = input.value.trim();
      saveState();
      showToast("URL базы сохранён");
      pullStateFromCloud(false);
    }

    function initCloudSync() {
      pullStateFromCloud(true);
      if (cloudSyncInterval) clearInterval(cloudSyncInterval);
      cloudSyncInterval = setInterval(() => {
        pullStateFromCloud(true);
      }, 5000);
    }

    /* ==============================================================
       GPS ГЕОЛОКАЦИЯ
       ============================================================== */
    function initGpsTracking() {
      try {
        if ("geolocation" in navigator) {
          navigator.geolocation.getCurrentPosition(
            pos => {
              currentGpsCoords = {
                lat: pos.coords.latitude.toFixed(6),
                lng: pos.coords.longitude.toFixed(6),
                accuracy: Math.round(pos.coords.accuracy)
              };
            },
            err => { currentGpsCoords = null; },
            { enableHighAccuracy: false, timeout: 5000, maximumAge: 60000 }
          );
        }
      } catch (e) {}
    }

    /* ==============================================================
       ВКЛАДКИ И РЕЖИМЫ
       ============================================================== */
    function switchTab(tabId) {
      document.querySelectorAll(".tab-content").forEach(el => el.classList.remove("active"));
      document.querySelectorAll(".tab-btn").forEach(el => el.classList.remove("active"));

      const target = document.getElementById(`tab-${tabId}`);
      if (target) target.classList.add("active");

      const btnMap = {
        foreman: "tabBtnForeman",
        docs: "tabBtnDocs",
        matrix: "tabBtnMatrix",
        rates: "tabBtnRates"
      };
      const activeBtn = document.getElementById(btnMap[tabId]);
      if (activeBtn) activeBtn.classList.add("active");

      if (tabId === "matrix") renderMatrixTable();
      if (tabId === "docs") renderUniversalDocsTable();
      if (tabId === "rates") {
        renderRatesTable();
        renderForemenRegistry();
        renderArchivedWorkersTable();
      }
    }

    function setShiftMode(mode) {
      shiftMode = mode;
      const startBtn = document.getElementById("modeStartBtn");
      const stopBtn = document.getElementById("modeStopBtn");
      const mainBtn = document.getElementById("mainActionBtn");
      const timeLbl = document.getElementById("declaredTimeLabel");
      const timeInp = document.getElementById("declaredTimeInput");
      const timeHint = document.getElementById("declaredTimeHint");
      const addBlock = document.getElementById("foremanAddWorkerBlock");

      selectedWorkerIds.clear();

      if (mode === "start") {
        startBtn.classList.add("active");
        stopBtn.classList.remove("active");
        mainBtn.className = "action-btn btn-start";
        mainBtn.innerHTML = "<span>НАЧАТЬ СМЕНУ</span>";
        if (timeLbl) timeLbl.innerText = "🕒 Время начала работы:";
        if (timeHint) timeHint.innerText = "";
        if (timeInp) {
          timeInp.removeAttribute("max");
          timeInp.value = getCurrentTimeStr();
        }
        if (addBlock) addBlock.style.display = "block";
      } else {
        stopBtn.classList.add("active");
        startBtn.classList.remove("active");
        mainBtn.className = "action-btn btn-stop";
        mainBtn.innerHTML = "<span>ЗАВЕРШИТЬ СМЕНУ</span>";
        if (timeLbl) timeLbl.innerText = "🕒 Время завершения работы:";
        if (timeHint) timeHint.innerText = "";
        if (timeInp) {
          const nowStr = getCurrentTimeStr();
          timeInp.value = nowStr;
          timeInp.setAttribute("max", nowStr);
        }
        if (addBlock) addBlock.style.display = "none";

        const today = getTodayKey();
        const myName = currentForemanUser ? currentForemanUser.name : "Ответственный";
        const combined = [
          ...foremenList.map(f => ({ ...f, isForeman: true })),
          ...employees.filter(e => !e.hiddenFromForemen).map(e => ({ ...e, isForeman: false }))
        ];
        combined.forEach(w => {
          const key = `${w.isForeman ? "f_" : "e_"}${w.id}`;
          const shift = shiftsDb[today]?.[key];
          if (shift && shift.startTime && !shift.endTime) {
            if (!currentForemanUser || shift.author === myName) {
              selectedWorkerIds.add(key);
            }
          }
        });
      }
      renderForemanWorkers();
    }

    /* ==============================================================
       СТИЛИ ПРОФЕССИЙ
       ============================================================== */
    function getRoleBadgeStyle(role) {
      const r = (role || "").toLowerCase();
      if (r.includes("эп") || r.includes("трактор") || r.includes("погруз")) {
        return "background: #f59e0b; color: #000; font-weight: 800;";
      }
      if (r.includes("гнб") || r.includes("бур")) {
        return "background: #ef4444; color: #fff; font-weight: 800;";
      }
      if (r.includes("монтаж")) {
        return "background: #3b82f6; color: #fff; font-weight: 800;";
      }
      if (r.includes("ответств") || r.includes("бригад")) {
        return "background: #8b5cf6; color: #fff; font-weight: 800;";
      }
      return "background: #22c55e; color: #000; font-weight: 800;";
    }

    /* ==============================================================
       ПУЛЬТ И СПИСОК РАБОЧИХ
       ============================================================== */
    function getTodayKey() {
      const now = new Date();
      const y = now.getFullYear();
      const m = String(now.getMonth() + 1).padStart(2, "0");
      const d = String(now.getDate()).padStart(2, "0");
      return `${y}-${m}-${d}`;
    }

    function renderObjectsSelect() {
      const sel = document.getElementById("foremanObjectSelect");
      if (!sel) return;
      sel.innerHTML = "";
      if (objectsList.length === 0) {
        const emptyOpt = document.createElement("option");
        emptyOpt.value = "";
        emptyOpt.innerText = "— Нет объектов (добавьте новый) —";
        sel.appendChild(emptyOpt);
        selectedObject = "";
        return;
      }
      objectsList.forEach(obj => {
        const opt = document.createElement("option");
        opt.value = obj;
        opt.innerText = obj;
        if (obj === selectedObject) opt.selected = true;
        sel.appendChild(opt);
      });
      if (!selectedObject && objectsList.length > 0) {
        selectedObject = objectsList[0];
      }
    }

    function changeForemanObject() {
      const sel = document.getElementById("foremanObjectSelect");
      if (sel) selectedObject = sel.value;
    }

    function addNewObjectPrompt() {
      const name = prompt("Введите наименование нового объекта:");
      if (!name || !name.trim()) return;
      const clean = name.trim();
      if (!objectsList.includes(clean)) {
        objectsList.push(clean);
        selectedObject = clean;
        saveState();
        pushStateToCloud();
        renderObjectsSelect();
        showToast(`Объект "${clean}" добавлен`);
      }
    }

    function renderForemanWorkers() {
      const container = document.getElementById("workersListMobile");
      if (!container) return;
      container.innerHTML = "";

      const today = getTodayKey();
      let hasAnyTodayShift = false;
      let activeCount = 0;
      const currentAuthor = currentForemanUser ? currentForemanUser.name : "Ответственный";

      const combined = [
        ...foremenList.map(f => ({ ...f, isForeman: true, role: f.role || "Ответственный" })),
        ...employees.filter(e => !e.hiddenFromForemen).map(e => ({ ...e, isForeman: false }))
      ];

      if (shiftMode === "stop") {
        combined.sort((a, b) => {
          const keyA = `${a.isForeman ? "f_" : "e_"}${a.id}`;
          const keyB = `${b.isForeman ? "f_" : "e_"}${b.id}`;
          const shiftA = shiftsDb[today]?.[keyA];
          const shiftB = shiftsDb[today]?.[keyB];

          const onShiftA = shiftA && shiftA.startTime && !shiftA.endTime;
          const onShiftB = shiftB && shiftB.startTime && !shiftB.endTime;

          const myA = onShiftA && (shiftA.author === currentAuthor);
          const myB = onShiftB && (shiftB.author === currentAuthor);

          if (myA && !myB) return -1;
          if (!myA && myB) return 1;
          if (onShiftA && !onShiftB) return -1;
          if (!onShiftA && onShiftB) return 1;
          return 0;
        });
      }

      combined.forEach(w => {
        const workerKey = `${w.isForeman ? "f_" : "e_"}${w.id}`;
        const shift = shiftsDb[today]?.[workerKey];
        const isOnShift = shift && shift.startTime && !shift.endTime;
        const isMyMorningWorker = isOnShift && (shift.author === currentAuthor);
        const isOnBreak = !!(isOnShift && shift.currentBreakStart);

        if (shift) hasAnyTodayShift = true;
        if (isOnShift && !isOnBreak) activeCount++;

        const isChecked = selectedWorkerIds.has(workerKey);

        const card = document.createElement("div");
        card.className = `worker-card ${isChecked ? "checked" : ""} ${isOnShift ? "on-shift" : ""}`;
        if (isOnBreak) {
          card.style.borderLeft = "4px solid #f59e0b";
        }
        card.onclick = () => toggleWorkerSelection(workerKey);

        const badgeStyle = getRoleBadgeStyle(w.role);

        let shiftInfoHtml = "";
        let liveTimerBadgeHtml = "";
        let breakActionHtml = "";

        if (shift) {
          if (isOnShift) {
            const authorTag = isMyMorningWorker 
              ? `<span style="color: #38bdf8; font-weight: 700;">★ Ваша утренняя смена</span>` 
              : `<span style="color: #94a3b8;">Открыл: ${shift.author || "Ответственный"}</span>`;

            let totalPastBreakMinutes = 0;
            if (shift.breaks && Array.isArray(shift.breaks)) {
              shift.breaks.forEach(b => {
                totalPastBreakMinutes += (b.minutes || 0);
              });
            }

            const breakStatusText = isOnBreak
              ? `<span style="color: #fde047; font-weight: 700;">⏸ В отлучке с ${shift.currentBreakStart}</span>`
              : (totalPastBreakMinutes > 0 ? `<span style="color: #cbd5e1;">(Отлучки: ${totalPastBreakMinutes} мин)</span>` : "");

            shiftInfoHtml = `
              <div style="font-size: 11px; margin-top: 3px; display: flex; align-items: center; gap: 6px; flex-wrap: wrap;">
                <span style="color: #86efac; font-weight: 600;">Старт: ${shift.startTime} (${shift.object || selectedObject})</span>
                <span style="color: #64748b;">•</span>
                ${authorTag}
                ${breakStatusText ? `<span style="color: #64748b;">•</span> ${breakStatusText}` : ""}
              </div>
            `;

            breakActionHtml = `
              <div style="margin-top: 8px;">
                <button type="button" class="action-btn" style="width: auto; padding: 4px 10px; font-size: 11px; font-weight: 700; ${isOnBreak ? 'background: linear-gradient(135deg, #16a34a, #15803d); color: #fff; border: 1px solid #4ade80;' : 'background: rgba(245, 158, 11, 0.15); color: #fde047; border: 1px solid #f59e0b;'}" onclick="event.stopPropagation(); toggleWorkerBreak('${workerKey}')">
                  ${isOnBreak ? '▶️ Вернулся (возобновить)' : '⏸ Отлучился по своим делам'}
                </button>
              </div>
            `;

            const timerColor = isOnBreak ? "#f59e0b" : "#38bdf8";
            const timerBorder = isOnBreak ? "#b45309" : "#0284c7";
            liveTimerBadgeHtml = `
              <div id="cardTimer_${workerKey}" style="font-size: 13px; font-weight: 800; font-family: monospace; color: ${timerColor}; background: #0f172a; border: 1px solid ${timerBorder}; padding: 4px 8px; border-radius: 6px; white-space: nowrap; margin-right: 8px;">
                ${isOnBreak ? '⏸ ПАУЗА' : '⏱ 00:00:00'}
              </div>
            `;
          } else if (shift.startTime && shift.endTime) {
            let totalPastBreakMinutes = 0;
            if (shift.breaks && Array.isArray(shift.breaks)) {
              shift.breaks.forEach(b => { totalPastBreakMinutes += (b.minutes || 0); });
            }
            const breaksLabel = totalPastBreakMinutes > 0 ? ` (отлучки: ${totalPastBreakMinutes} мин)` : "";
            shiftInfoHtml = `
              <div style="font-size: 11px; color: #94a3b8; margin-top: 4px;">
                ✓ Смена закрыта: ${shift.startTime} – ${shift.endTime}${breaksLabel} (итог: <b style="color: #cbd5e1;">${shift.totalHours || 0} ч</b>)
              </div>
            `;
          }
        }

        card.innerHTML = `
          <div style="flex: 1; padding-right: 8px;">
            <div class="worker-name">
              <span>${w.name}</span>
              <span style="font-size: 10px; padding: 2px 6px; border-radius: 4px; ${badgeStyle}">${w.role}</span>
              ${w.phone ? `<span style="font-size: 11px; color: #64748b; font-weight: normal;">${w.phone}</span>` : ""}
            </div>
            ${shiftInfoHtml}
            ${breakActionHtml}
          </div>
          <div style="display: flex; align-items: center; gap: 4px;">
            ${liveTimerBadgeHtml}
            <div class="custom-checkbox">
              <span class="chk-icon">${isChecked ? "✓" : "+"}</span>
              <span>${isChecked ? "Выбран" : "Выбрать"}</span>
            </div>
          </div>
        `;

        container.appendChild(card);
      });

      const mistakeBtn = document.getElementById("btnForemanMistake");
      if (mistakeBtn) {
        mistakeBtn.style.display = hasAnyTodayShift ? "flex" : "none";
      }

      const liveBanner = document.getElementById("liveShiftActiveBanner");
      const liveCount = document.getElementById("liveShiftCountText");
      if (liveBanner && liveCount) {
        if (activeCount > 0) {
          liveBanner.style.display = "flex";
          liveCount.innerText = `На объекте: ${activeCount} чел.`;
        } else {
          liveBanner.style.display = "none";
        }
      }
    }

    /* ==============================================================
       УПРАВЛЕНИЕ ПАУЗАМИ (ОТЛУЧИЛСЯ ПО СВОИМ ДЕЛАМ)
       ============================================================== */
    function toggleWorkerBreak(workerKey) {
      const today = getTodayKey();
      const shift = shiftsDb[today]?.[workerKey];
      if (!shift || !shift.startTime || shift.endTime) {
        showToast("Смена не активна");
        return;
      }

      const nowTime = getCurrentTimeStr();
      const author = currentForemanUser ? currentForemanUser.name : "Ответственный";

      if (!shift.breaks) shift.breaks = [];
      if (!shift.corrections) shift.corrections = [];

      if (!shift.currentBreakStart) {
        shift.currentBreakStart = nowTime;
        shift.corrections.push({
          date: new Date().toLocaleTimeString("ru-RU", { hour: "2-digit", minute: "2-digit" }),
          author,
          action: `⏸ Отлучился по своим делам в ${nowTime} (время приостановлено)`
        });
        showToast(`⏸ Зафиксирована отлучка в ${nowTime}`);
      } else {
        const breakStart = shift.currentBreakStart;
        const [h1, m1] = breakStart.split(":").map(Number);
        const [h2, m2] = nowTime.split(":").map(Number);
        let diffMin = (h2 * 60 + m2) - (h1 * 60 + m1);
        if (diffMin < 0) diffMin += 24 * 60;

        shift.breaks.push({
          start: breakStart,
          end: nowTime,
          minutes: diffMin
        });

        shift.currentBreakStart = null;
        shift.corrections.push({
          date: new Date().toLocaleTimeString("ru-RU", { hour: "2-digit", minute: "2-digit" }),
          author,
          action: `▶️ Вернулся на объект в ${nowTime} (отсутствовал ${diffMin} мин)`
        });
        showToast(`▶️ Возвращение зафиксировано (${diffMin} мин отсутствия вычтено)`);
      }

      saveState();
      pushStateToCloud();
      renderForemanWorkers();
      renderMatrixTable();
    }

    function toggleWorkerSelection(workerKey) {
      if (selectedWorkerIds.has(workerKey)) {
        selectedWorkerIds.delete(workerKey);
      } else {
        selectedWorkerIds.add(workerKey);
      }
      renderForemanWorkers();
    }

    function addWorkerByForeman() {
      const nameInp = document.getElementById("quickWorkerName");
      const roleInp = document.getElementById("quickWorkerRole");
      const phoneInp = document.getElementById("quickWorkerPhone");

      const name = nameInp ? nameInp.value.trim() : "";
      const role = roleInp ? roleInp.value.trim() || "Самозанятый" : "Самозанятый";
      const phone = phoneInp ? phoneInp.value.trim() : "";

      if (!name) {
        showToast("Укажите ФИО самозанятого");
        return;
      }

      const isSmzRole = role.toLowerCase().includes("самозанят") || role.toLowerCase().includes("разнораб") || role.toLowerCase().includes("подсоб");
      const initialRate = isSmzRole ? 500 : 750;

      const now = new Date();
      const newEmp = {
        id: Date.now(),
        name,
        role,
        phone,
        rate: initialRate,
        startMonth: now.getMonth() + 1,
        startYear: now.getFullYear(),
        hiddenFromForemen: false,
        addedBy: currentForemanUser ? currentForemanUser.name : "Ответственный на объекте"
      };

      employees.push(newEmp);
      selectedWorkerIds.add(`e_${newEmp.id}`);

      if (nameInp) nameInp.value = "";
      if (roleInp) roleInp.value = "";
      if (phoneInp) phoneInp.value = "";

      saveState();
      pushStateToCloud();
      renderForemanWorkers();
      renderRatesTable();
      renderMatrixTable();
      showToast(`Самозанятый ${name} добавлен (ставка 4000 ₽ / 8ч + обед)`);
    }

    /* ==============================================================
       ДЕЙСТВИЯ СО СМЕНОЙ
       ============================================================== */
    function executeShiftAction() {
      if (selectedWorkerIds.size === 0) {
        showToast("Выберите хотя бы одного исполнителя");
        return;
      }

      const timeInp = document.getElementById("declaredTimeInput");
      const declaredTime = timeInp && timeInp.value ? timeInp.value : getCurrentTimeStr();
      const realNowTime = getCurrentTimeStr();
      const author = currentForemanUser ? currentForemanUser.name : "Ответственный";

      if (shiftMode === "stop") {
        const [decH, decM] = declaredTime.split(":").map(Number);
        const [nowH, nowM] = realNowTime.split(":").map(Number);
        const decTotal = decH * 60 + decM;
        const nowTotal = nowH * 60 + nowM;

        if (decTotal > nowTotal) {
          showToast(`⚠️ Нельзя завершить смену будущим временем! Сейчас ${realNowTime}`);
          if (timeInp) timeInp.value = realNowTime;
          return;
        }
      }

      const today = getTodayKey();
      if (!shiftsDb[today]) shiftsDb[today] = {};

      let updatedCount = 0;

      selectedWorkerIds.forEach(workerKey => {
        let shift = shiftsDb[today][workerKey];

        if (shiftMode === "start") {
          if (shift && shift.startTime && !shift.endTime) {
            return;
          }
          shiftsDb[today][workerKey] = {
            object: selectedObject,
            startTime: declaredTime,
            endTime: null,
            totalHours: 0,
            originalActualPressStart: realNowTime,
            gpsStart: currentGpsCoords ? `${currentGpsCoords.lat},${currentGpsCoords.lng}` : null,
            author,
            corrections: []
          };
          updatedCount++;
        } else {
          if (!shift || !shift.startTime) return;
          if (shift.endTime) return;

          if (shift.currentBreakStart) {
            const breakStart = shift.currentBreakStart;
            const [h1, m1] = breakStart.split(":").map(Number);
            const [h2, m2] = declaredTime.split(":").map(Number);
            let diffMin = (h2 * 60 + m2) - (h1 * 60 + m1);
            if (diffMin < 0) diffMin += 24 * 60;
            if (!shift.breaks) shift.breaks = [];
            shift.breaks.push({ start: breakStart, end: declaredTime, minutes: diffMin });
            shift.currentBreakStart = null;
          }

          shift.endTime = declaredTime;
          shift.originalActualPressEnd = realNowTime;
          shift.gpsEnd = currentGpsCoords ? `${currentGpsCoords.lat},${currentGpsCoords.lng}` : null;
          
          const isForemanWorker = workerKey.startsWith("f_");
          const shouldDeductLunch = !isForemanWorker;
          shift.totalHours = calculateHoursBetween(shift.startTime, shift.endTime, shouldDeductLunch, shift.breaks);
          updatedCount++;
        }
      });

      if (updatedCount === 0) {
        if (shiftMode === "start") {
          showToast("Смена уже открыта! Для правок используйте «Я ошибся»");
        } else {
          showToast("Смена уже закрыта или не была открыта");
        }
        return;
      }

      selectedWorkerIds.clear();
      saveState();
      pushStateToCloud();
      renderForemanWorkers();
      renderMatrixTable();
      showToast(shiftMode === "start" ? `Смена открыта (${updatedCount} чел.)` : `Смена завершена (${updatedCount} чел.)`);
    }

    function getCurrentTimeStr() {
      const now = new Date();
      return `${String(now.getHours()).padStart(2, "0")}:${String(now.getMinutes()).padStart(2, "0")}`;
    }

    function calculateHoursBetween(start, end, deductLunch = true, breaksList = []) {
      if (!start || !end) return 0;
      const [h1, m1] = start.split(":").map(Number);
      const [h2, m2] = end.split(":").map(Number);
      let diff = (h2 * 60 + m2) - (h1 * 60 + m1);
      if (diff < 0) diff += 24 * 60;

      let totalBreakMinutes = 0;
      if (Array.isArray(breaksList)) {
        breaksList.forEach(b => {
          totalBreakMinutes += (Number(b.minutes) || 0);
        });
      }

      diff = Math.max(0, diff - totalBreakMinutes);
      let totalGrossHours = diff / 60;

      // Автоматический вычет 1 часа обеда только при сменах от 8 часов
      if (deductLunch && totalGrossHours >= 8) {
        totalGrossHours = Math.max(0, totalGrossHours - 1);
      }

      return +totalGrossHours.toFixed(2);
    }

    /* ==============================================================
       ТАЙМЕРЫ НА КАРТОЧКАХ
       ============================================================== */
    function initLiveTimersLoop() {
      setInterval(() => {
        const today = getTodayKey();
        const now = new Date();
        const nowSec = (now.getHours() * 3600) + (now.getMinutes() * 60) + now.getSeconds();

        let oldestStartMinutes = null;
        let anyActive = false;

        const combined = [
          ...foremenList.map(f => ({ ...f, isForeman: true })),
          ...employees.map(e => ({ ...e, isForeman: false }))
        ];

        for (let i = 0; i < combined.length; i++) {
          const w = combined[i];
          const key = `${w.isForeman ? "f_" : "e_"}${w.id}`;
          const shift = shiftsDb[today]?.[key];
          const cardTimerEl = document.getElementById(`cardTimer_${key}`);

          if (shift && shift.startTime && !shift.endTime) {
            anyActive = true;
            const [sh, sm] = shift.startTime.split(":").map(Number);
            const startSec = (sh * 3600) + (sm * 60);
            let elapsed = nowSec - startSec;
            if (elapsed < 0) elapsed += 24 * 3600;

            let completedBreakSec = 0;
            if (shift.breaks && Array.isArray(shift.breaks)) {
              for (let b = 0; b < shift.breaks.length; b++) {
                completedBreakSec += (shift.breaks[b].minutes || 0) * 60;
              }
            }

            if (shift.currentBreakStart) {
              const [cbH, cbM] = shift.currentBreakStart.split(":").map(Number);
              const cbStartSec = (cbH * 3600) + (cbM * 60);
              let curBreakSec = nowSec - cbStartSec;
              if (curBreakSec < 0) curBreakSec += 24 * 3600;
              completedBreakSec += curBreakSec;
            }

            elapsed = Math.max(0, elapsed - completedBreakSec);

            const eh = Math.floor(elapsed / 3600);
            const em = Math.floor((elapsed % 3600) / 60);
            const es = elapsed % 60;

            const timeFormatted = `${String(eh).padStart(2, "0")}:${String(em).padStart(2, "0")}:${String(es).padStart(2, "0")}`;

            if (cardTimerEl) {
              const targetText = shift.currentBreakStart ? `⏸ ПАУЗА ${timeFormatted}` : `⏱ ${timeFormatted}`;
              if (cardTimerEl.textContent !== targetText) {
                cardTimerEl.textContent = targetText;
              }
            }

            if (!shift.currentBreakStart) {
              if (oldestStartMinutes === null || startSec < oldestStartMinutes) {
                oldestStartMinutes = startSec;
              }
            }
          }
        }

        const globalTimer = document.getElementById("liveShiftGlobalTimer");
        if (globalTimer && anyActive && oldestStartMinutes !== null) {
          let elapsed = nowSec - oldestStartMinutes;
          if (elapsed < 0) elapsed += 24 * 3600;
          const gh = String(Math.floor(elapsed / 3600)).padStart(2, "0");
          const gm = String(Math.floor((elapsed % 3600) / 60)).padStart(2, "0");
          const gs = String(elapsed % 60).padStart(2, "0");
          const formatted = `${gh}:${gm}:${gs}`;
          if (globalTimer.textContent !== formatted) {
            globalTimer.textContent = formatted;
          }
        }
      }, 1000);
    }

    /* ==============================================================
       «Я ОШИБСЯ»
       ============================================================== */
    function openMistakeModal() {
      const today = getTodayKey();
      const select = document.getElementById("mistakeWorkerSelect");
      if (!select) return;
      select.innerHTML = "";

      const combined = [
        ...foremenList.map(f => ({ ...f, isForeman: true, role: f.role || "Ответственный" })),
        ...employees.map(e => ({ ...e, isForeman: false }))
      ];

      let count = 0;
      combined.forEach(w => {
        const key = `${w.isForeman ? "f_" : "e_"}${w.id}`;
        const shift = shiftsDb[today]?.[key];
        if (shift) {
          const opt = document.createElement("option");
          opt.value = key;
          opt.innerText = `${w.name} (${w.role}) — ${shift.startTime || ""}-${shift.endTime || "..."}`;
          select.appendChild(opt);
          count++;
        }
      });

      if (count === 0) {
        showToast("Сегодня ещё нет открытых или закрытых смен");
        return;
      }

      document.getElementById("mistakeObjectInput").value = selectedObject;
      document.getElementById("mistakeReasonInput").value = "";
      document.getElementById("mistakeModal").classList.add("open");
    }

    function closeMistakeModal() {
      const m = document.getElementById("mistakeModal");
      if (m) m.classList.remove("open");
    }

    function submitMistakeCorrection() {
      const select = document.getElementById("mistakeWorkerSelect");
      const startInp = document.getElementById("mistakeStartInput");
      const endInp = document.getElementById("mistakeEndInput");
      const objInp = document.getElementById("mistakeObjectInput");
      const reasonInp = document.getElementById("mistakeReasonInput");

      const key = select ? select.value : null;
      const today = getTodayKey();
      const shift = shiftsDb[today]?.[key];

      if (!shift) {
        showToast("Смена не найдена");
        return;
      }

      const reason = reasonInp ? reasonInp.value.trim() : "";
      if (!reason) {
        showToast("Укажите причину ошибки / уточнения");
        return;
      }

      const prevStart = shift.startTime;
      const prevEnd = shift.endTime;

      if (startInp && startInp.value) shift.startTime = startInp.value;
      if (endInp && endInp.value) shift.endTime = endInp.value;
      if (objInp && objInp.value) shift.object = objInp.value.trim();

      if (shift.startTime && shift.endTime) {
        const isForemanWorker = key.startsWith("f_");
        shift.totalHours = calculateHoursBetween(shift.startTime, shift.endTime, !isForemanWorker, shift.breaks || []);
      }

      if (!shift.corrections) shift.corrections = [];
      const author = currentForemanUser ? currentForemanUser.name : "Ответственный";
      shift.corrections.push({
        date: new Date().toLocaleTimeString("ru-RU", { hour: "2-digit", minute: "2-digit" }),
        author,
        action: `Время скорректировано с [${prevStart || "—"}–${prevEnd || "—"}] на [${shift.startTime || "—"}–${shift.endTime || "—"}]. Причина: ${reason}`
      });

      closeMistakeModal();
      saveState();
      pushStateToCloud();
      renderForemanWorkers();
      renderMatrixTable();
      showToast("Уточнение принято и отправлено в табель");
    }

    /* ==============================================================
       ФОТООТЧЕТ И ЧЕКИ
       ============================================================== */
    function handleUniversalDocUpload(event) {
      const file = event.target.files[0];
      if (!file) return;

      const reader = new FileReader();
      reader.onload = function(e) {
        const img = new Image();
        img.onload = function() {
          const canvas = document.createElement("canvas");
          const maxDim = 1200;
          let w = img.width;
          let h = img.height;
          if (w > h && w > maxDim) {
            h = Math.round((h * maxDim) / w);
            w = maxDim;
          } else if (h > maxDim) {
            w = Math.round((w * maxDim) / h);
            h = maxDim;
          }
          canvas.width = w;
          canvas.height = h;
          const ctx = canvas.getContext("2d");
          ctx.drawImage(img, 0, 0, w, h);
          const compressedDataUrl = canvas.toDataURL("image/jpeg", 0.7);

          const now = new Date();
          const docItem = {
            id: Date.now(),
            date: now.toLocaleDateString("ru-RU"),
            time: now.toLocaleTimeString("ru-RU", { hour: "2-digit", minute: "2-digit" }),
            object: selectedObject,
            foreman: currentForemanUser ? currentForemanUser.name : "Ответственный",
            imageUrl: compressedDataUrl
          };

          universalDocs.unshift(docItem);
          saveState();
          pushStateToCloud();
          renderUniversalDocsTable();
          showToast("📸 Документ сохранён и прикреплён к объекту");
        };
        img.src = e.target.result;
      };
      reader.readAsDataURL(file);
      event.target.value = "";
    }

    function renderUniversalDocsTable() {
      const tbody = document.getElementById("universalDocsTableBody");
      if (!tbody) return;
      tbody.innerHTML = "";

      if (universalDocs.length === 0) {
        tbody.innerHTML = `<tr><td colspan="6" style="padding: 20px; color: var(--text-muted);">Нет прикреплённых документов</td></tr>`;
        return;
      }

      universalDocs.forEach((doc, idx) => {
        const tr = document.createElement("tr");
        tr.innerHTML = `
          <td>${idx + 1}</td>
          <td>${doc.date} <span style="color: var(--accent-cyan);">${doc.time}</span></td>
          <td><b>${doc.object}</b></td>
          <td>${doc.foreman}</td>
          <td>
            <img src="${doc.imageUrl}" style="width: 44px; height: 44px; object-fit: cover; border-radius: 4px; cursor: pointer; border: 1px solid var(--border-color);" onclick="openPhotoViewModal('${doc.id}')">
          </td>
          <td>
            <button class="action-btn" style="padding: 4px 8px; font-size: 11px; background: #dc2626; color: #fff; width: auto;" onclick="deleteUniversalDoc(${doc.id})">Удалить</button>
          </td>
        `;
        tbody.appendChild(tr);
      });
    }

    function openPhotoViewModal(docId) {
      const doc = universalDocs.find(d => d.id == docId);
      if (!doc) return;
      const img = document.getElementById("photoViewImg");
      const m = document.getElementById("photoViewModal");
      if (img && m) {
        img.src = doc.imageUrl;
        m.classList.add("open");
      }
    }

    function closePhotoViewModal() {
      const m = document.getElementById("photoViewModal");
      if (m) m.classList.remove("open");
    }

    function deleteUniversalDoc(id) {
      if (!confirm("Удалить фото документа?")) return;
      universalDocs = universalDocs.filter(d => d.id !== id);
      saveState();
      pushStateToCloud();
      renderUniversalDocsTable();
      showToast("Документ удалён");
    }

    function exportDocsToCsv() {
      let csv = "№;Дата;Время;Объект;Ответственный\n";
      universalDocs.forEach((d, i) => {
        csv += `${i + 1};${d.date};${d.time};"${d.object}";"${d.foreman}"\n`;
      });
      downloadCsv(csv, `docs_${new Date().toISOString().slice(0, 10)}.csv`);
    }

    /* ==============================================================
       ТАБЕЛЬ (ШАХМАТКА)
       ============================================================== */
    function changeMonth(delta) {
      currentMonth += delta;
      if (currentMonth > 12) {
        currentMonth = 1;
        currentYear++;
      } else if (currentMonth < 1) {
        currentMonth = 12;
        currentYear--;
      }
      renderMatrixTable();
    }

    function renderMatrixTable() {
      const table = document.getElementById("fullMatrixTable");
      const label = document.getElementById("matrixMonthLabel");
      if (!table) return;

      const monthsNames = ["Январь", "Февраль", "Март", "Апрель", "Май", "Июнь", "Июль", "Август", "Сентябрь", "Октябрь", "Ноябрь", "Декабрь"];
      if (label) label.innerText = `${monthsNames[currentMonth - 1]} ${currentYear}`;

      const daysInMonth = new Date(currentYear, currentMonth, 0).getDate();

      let visibleWorkers = [];
      if (currentForemanUser) {
        visibleWorkers = [{ ...currentForemanUser, isForeman: true, role: currentForemanUser.role || "Ответственный" }];
      } else {
        visibleWorkers = [
          ...foremenList.map(f => ({ ...f, isForeman: true, role: f.role || "Ответственный" })),
          ...employees.map(e => ({ ...e, isForeman: false }))
        ];
      }

      let html = "<thead><tr>";
      html += "<th class=\"sticky-col-1\">ФИО Исполнителя</th>";
      html += "<th class=\"sticky-col-2\">Специальность</th>";
      html += "<th class=\"sticky-col-3\">Показатель</th>";

      for (let d = 1; d <= daysInMonth; d++) {
        const dateObj = new Date(currentYear, currentMonth - 1, d);
        const isWeekend = dateObj.getDay() === 0 || dateObj.getDay() === 6;
        html += `<th class="${isWeekend ? "weekend-col" : ""}">${d}</th>`;
      }
      html += "<th class=\"summary-cell\">ИТОГО</th></tr></thead><tbody>";

      visibleWorkers.forEach(w => {
        const workerKey = `${w.isForeman ? "f_" : "e_"}${w.id}`;
        const rate = Number(w.rate) || 0;

        let totalMonthHours = 0;
        const daysData = [];

        for (let d = 1; d <= daysInMonth; d++) {
          const dateStr = `${currentYear}-${String(currentMonth).padStart(2, "0")}-${String(d).padStart(2, "0")}`;
          const shift = shiftsDb[dateStr]?.[workerKey];
          daysData.push({ dateStr, shift });
          if (shift && shift.totalHours) {
            totalMonthHours += Number(shift.totalHours);
          }
        }

        const totalEarn = Math.round(totalMonthHours * rate);

        // Строка 1: Часы
        html += `<tr><td rowspan="5" class="sticky-col-1">${w.name}</td><td rowspan="5" class="sticky-col-2">${w.role}</td><td class="sticky-col-3" style="color: #38bdf8;">Часы</td>`;
        daysData.forEach(item => {
          const h = item.shift ? (item.shift.totalHours || 0) : "";
          const hasNotes = item.shift && item.shift.corrections && item.shift.corrections.length > 0;
          html += `<td class="editable-day" onclick="openShiftEditModal('${w.name}', '${item.dateStr}', '${workerKey}')">${h ? `${h}${hasNotes ? "📝" : ""}` : "·"}</td>`;
        });
        html += `<td class="summary-cell" style="color: #38bdf8;">${totalMonthHours.toFixed(1)} ч</td></tr>`;

        // Строка 2: Объект
        html += `<tr><td class="sticky-col-3" style="color: #94a3b8;">Объект</td>`;
        daysData.forEach(item => {
          const obj = item.shift && item.shift.object ? item.shift.object.slice(0, 7) : "";
          html += `<td style="font-size: 10px; color: #94a3b8;">${obj || "·"}</td>`;
        });
        html += `<td class="summary-cell">—</td></tr>`;

        // Строка 3: Ответственный
        html += `<tr><td class="sticky-col-3" style="color: #c084fc;">Ответственный</td>`;
        daysData.forEach(item => {
          const auth = item.shift && item.shift.author ? item.shift.author : "";
          const shortAuth = auth ? (auth.split(" ")[0] || auth) : "";
          html += `<td style="font-size: 10px; color: #c084fc; font-weight: 600;" title="${auth ? 'Отписал: ' + auth : ''}">${shortAuth || "·"}</td>`;
        });
        html += `<td class="summary-cell">—</td></tr>`;

        // Строка 4: Уточнения
        html += `<tr><td class="sticky-col-3" style="color: #fde047;">Уточнения</td>`;
        daysData.forEach(item => {
          const count = item.shift && item.shift.corrections ? item.shift.corrections.length : 0;
          html += `<td style="font-size: 10px; color: #fde047;">${count > 0 ? `⚠️ (${count})` : "·"}</td>`;
        });
        html += `<td class="summary-cell">—</td></tr>`;

        // Строка 5: Заработок
        html += `<tr><td class="sticky-col-3" style="color: #4ade80;">Заработок</td>`;
        daysData.forEach(item => {
          const h = item.shift ? (item.shift.totalHours || 0) : 0;
          const sum = Math.round(h * rate);
          html += `<td style="font-size: 11px; color: #4ade80;">${sum ? sum : "·"}</td>`;
        });
        html += `<td class="summary-cell" style="color: #4ade80;">${totalEarn.toLocaleString("ru-RU")} ₽</td></tr>`;
      });

      html += "</tbody>";
      table.innerHTML = html;
    }

    function openShiftEditModal(workerName, dateStr, workerKey) {
      if (currentForemanUser) return;

      editingShiftContext = { workerName, dateStr, workerKey };
      const shift = shiftsDb[dateStr]?.[workerKey];

      document.getElementById("editModalTitle").innerText = `${workerName} — ${dateStr}`;
      document.getElementById("modalObject").value = shift ? (shift.object || "") : selectedObject;
      document.getElementById("modalStart").value = shift ? (shift.startTime || "") : "08:00";
      document.getElementById("modalEnd").value = shift ? (shift.endTime || "") : "18:00";

      const auditBox = document.getElementById("modalAuditBlock");
      if (auditBox) {
        if (shift) {
          let auditHtml = `<div>👤 <b>Ответственный за смену:</b> <span style="color: #38bdf8; font-weight: 700;">${shift.author || "Не указан"}</span></div>`;
          auditHtml += `<div style="margin-top: 4px;">🔒 <b>Факт нажатия:</b> Старт ${shift.originalActualPressStart || "—"} | Финиш ${shift.originalActualPressEnd || "—"}</div>`;
          if (shift.gpsStart) auditHtml += `<div>📍 GPS: ${shift.gpsStart}</div>`;
          if (shift.corrections && shift.corrections.length > 0) {
            auditHtml += `<div style="margin-top: 6px; color: #fde047;"><b>Примечания и уточнения:</b></div>`;
            shift.corrections.forEach(c => {
              auditHtml += `<div style="font-size: 11px; color: #cbd5e1; margin-top: 2px;">• [${c.date}, ${c.author}]: ${c.action}</div>`;
            });
          }
          auditBox.innerHTML = auditHtml;
        } else {
          auditBox.innerHTML = `<span style="color: var(--text-muted);">Смена ещё не зафиксирована</span>`;
        }
      }

      document.getElementById("editModal").classList.add("open");
    }

    function closeEditModal() {
      const m = document.getElementById("editModal");
      if (m) m.classList.remove("open");
      editingShiftContext = null;
    }

    function saveModalEdit() {
      if (!editingShiftContext) return;
      const { dateStr, workerKey } = editingShiftContext;

      if (!shiftsDb[dateStr]) shiftsDb[dateStr] = {};
      const obj = document.getElementById("modalObject").value.trim();
      const start = document.getElementById("modalStart").value;
      const end = document.getElementById("modalEnd").value;

      let shift = shiftsDb[dateStr][workerKey];
      const isForemanWorker = workerKey.startsWith("f_");
      const shouldDeductLunch = !isForemanWorker;

      if (!shift) {
        shift = {
          object: obj,
          startTime: start,
          endTime: end,
          totalHours: calculateHoursBetween(start, end, shouldDeductLunch),
          originalActualPressStart: getCurrentTimeStr(),
          author: "Администратор",
          breaks: [],
          corrections: []
        };
      } else {
        if (!shift.corrections) shift.corrections = [];
        shift.corrections.push({
          date: new Date().toLocaleTimeString("ru-RU", { hour: "2-digit", minute: "2-digit" }),
          author: "Администратор",
          action: `Правка табеля: объект "${obj}", время [${start}–${end}]`
        });
        shift.object = obj;
        shift.startTime = start;
        shift.endTime = end;
        shift.totalHours = calculateHoursBetween(start, end, shouldDeductLunch, shift.breaks || []);
      }

      shiftsDb[dateStr][workerKey] = shift;
      closeEditModal();
      saveState();
      pushStateToCloud();
      renderMatrixTable();
      renderForemanWorkers();
      showToast("Смена сохранена");
    }

    function deleteModalShift() {
      if (!editingShiftContext) return;
      if (!confirm("Удалить отметку смены?")) return;
      const { dateStr, workerKey } = editingShiftContext;
      if (shiftsDb[dateStr]?.[workerKey]) {
        delete shiftsDb[dateStr][workerKey];
      }
      closeEditModal();
      saveState();
      pushStateToCloud();
      renderMatrixTable();
      renderForemanWorkers();
      showToast("Смена удалена");
    }

    function exportMatrixToCsv() {
      const daysInMonth = new Date(currentYear, currentMonth, 0).getDate();
      const monthsNames = ["Январь", "Февраль", "Март", "Апрель", "Май", "Июнь", "Июль", "Август", "Сентябрь", "Октябрь", "Ноябрь", "Декабрь"];
      const currentMonthName = monthsNames[currentMonth - 1];

      let visible = currentForemanUser
        ? [{ ...currentForemanUser, isForeman: true, role: currentForemanUser.role || "Ответственный" }]
        : [
            ...foremenList.map(f => ({ ...f, isForeman: true, role: f.role || "Ответственный" })),
            ...employees.map(e => ({ ...e, isForeman: false }))
          ];

      const fileName = currentForemanUser
        ? `Табель_${currentForemanUser.name}_${String(currentMonth).padStart(2, '0')}.${currentYear}.xls`
        : `Табель_${String(currentMonth).padStart(2, '0')}.${currentYear}.xls`;

      let xml = `<?xml version="1.0" encoding="UTF-8"?>
<?mso-application progid="Excel.Sheet"?>
<Workbook xmlns="urn:schemas-microsoft-com:office:spreadsheet"
 xmlns:o="urn:schemas-microsoft-com:office:office"
 xmlns:x="urn:schemas-microsoft-com:office:excel"
 xmlns:ss="urn:schemas-microsoft-com:office:spreadsheet"
 xmlns:html="http://www.w3.org/TR/REC-html40">
 <DocumentProperties xmlns="urn:schemas-microsoft-com:office:office">
  <Title>Табель учета рабочего времени</Title>
  <Author>Activity Hub</Author>
  <Created>${new Date().toISOString()}</Created>
 </DocumentProperties>
 <Styles>
  <Style ss:ID="Default" ss:Name="Normal">
   <Alignment ss:Vertical="Center"/>
   <Borders/>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="11" ss:Color="#000000"/>
   <Interior/>
   <NumberFormat/>
   <Protection/>
  </Style>
  <Style ss:ID="TitleStyle">
   <Alignment ss:Horizontal="Left" ss:Vertical="Center"/>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="14" ss:Bold="1" ss:Color="#1E293B"/>
  </Style>
  <Style ss:ID="HeaderCol">
   <Alignment ss:Horizontal="Center" ss:Vertical="Center" ss:WrapText="1"/>
   <Borders>
    <Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
   </Borders>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="10" ss:Bold="1" ss:Color="#0F172A"/>
   <Interior ss:Color="#E2E8F0" ss:Pattern="Solid"/>
  </Style>
  <Style ss:ID="HeaderColWeekend">
   <Alignment ss:Horizontal="Center" ss:Vertical="Center" ss:WrapText="1"/>
   <Borders>
    <Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
   </Borders>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="10" ss:Bold="1" ss:Color="#B91C1C"/>
   <Interior ss:Color="#FEE2E2" ss:Pattern="Solid"/>
  </Style>
  <Style ss:ID="HeaderTotal">
   <Alignment ss:Horizontal="Center" ss:Vertical="Center"/>
   <Borders>
    <Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
   </Borders>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="10" ss:Bold="1" ss:Color="#0369A1"/>
   <Interior ss:Color="#BAE6FD" ss:Pattern="Solid"/>
  </Style>
  <Style ss:ID="CellFio">
   <Alignment ss:Horizontal="Left" ss:Vertical="Center" ss:Indent="1"/>
   <Borders>
    <Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
    <Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
    <Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
    <Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
   </Borders>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="10" ss:Bold="1" ss:Color="#0F172A"/>
   <Interior ss:Color="#FFFFFF" ss:Pattern="Solid"/>
  </Style>
  <Style ss:ID="CellRole">
   <Alignment ss:Horizontal="Left" ss:Vertical="Center" ss:Indent="1"/>
   <Borders>
    <Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
    <Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
    <Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
    <Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
   </Borders>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="9" ss:Color="#475569"/>
   <Interior ss:Color="#F8FAFC" ss:Pattern="Solid"/>
  </Style>
  <Style ss:ID="CellMetric">
   <Alignment ss:Horizontal="Center" ss:Vertical="Center"/>
   <Borders>
    <Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
    <Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
    <Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
    <Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
   </Borders>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="9" ss:Bold="1" ss:Color="#334155"/>
   <Interior ss:Color="#F1F5F9" ss:Pattern="Solid"/>
  </Style>
  <Style ss:ID="CellHours">
   <Alignment ss:Horizontal="Center" ss:Vertical="Center"/>
   <Borders>
    <Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#E2E8F0"/>
    <Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#E2E8F0"/>
    <Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#E2E8F0"/>
    <Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#E2E8F0"/>
   </Borders>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="10" ss:Bold="1" ss:Color="#0284C7"/>
   <Interior ss:Color="#FFFFFF" ss:Pattern="Solid"/>
  </Style>
  <Style ss:ID="CellHoursWeekend">
   <Alignment ss:Horizontal="Center" ss:Vertical="Center"/>
   <Borders>
    <Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#E2E8F0"/>
    <Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#E2E8F0"/>
    <Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#E2E8F0"/>
    <Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#E2E8F0"/>
   </Borders>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="10" ss:Bold="1" ss:Color="#0284C7"/>
   <Interior ss:Color="#FEF2F2" ss:Pattern="Solid"/>
  </Style>
  <Style ss:ID="CellObj">
   <Alignment ss:Horizontal="Center" ss:Vertical="Center"/>
   <Borders>
    <Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#E2E8F0"/>
    <Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#E2E8F0"/>
    <Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#E2E8F0"/>
    <Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#E2E8F0"/>
   </Borders>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="8" ss:Color="#64748B"/>
   <Interior ss:Color="#FFFFFF" ss:Pattern="Solid"/>
  </Style>
  <Style ss:ID="CellSum">
   <Alignment ss:Horizontal="Center" ss:Vertical="Center"/>
   <Borders>
    <Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
    <Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
    <Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
    <Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#CBD5E1"/>
   </Borders>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="9" ss:Color="#15803D"/>
   <Interior ss:Color="#FFFFFF" ss:Pattern="Solid"/>
   <NumberFormat ss:Format="#,##0"/>
  </Style>
  <Style ss:ID="CellTotalHours">
   <Alignment ss:Horizontal="Center" ss:Vertical="Center"/>
   <Borders>
    <Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
   </Borders>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="10" ss:Bold="1" ss:Color="#0369A1"/>
   <Interior ss:Color="#E0F2FE" ss:Pattern="Solid"/>
  </Style>
  <Style ss:ID="CellTotalMoney">
   <Alignment ss:Horizontal="Right" ss:Vertical="Center" ss:Indent="1"/>
   <Borders>
    <Border ss:Position="Bottom" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Left" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Right" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
    <Border ss:Position="Top" ss:LineStyle="Continuous" ss:Weight="1" ss:Color="#94A3B8"/>
   </Borders>
   <Font ss:FontName="Calibri" x:CharSet="204" ss:Size="10" ss:Bold="1" ss:Color="#166534"/>
   <Interior ss:Color="#DCFCE7" ss:Pattern="Solid"/>
   <NumberFormat ss:Format="#,##0\ &quot;₽&quot;"/>
  </Style>
 </Styles>
 <Worksheet ss:Name="${currentMonthName} ${currentYear}">
  <Table ss:DefaultRowHeight="20">
   <Column ss:Width="30"/>
   <Column ss:Width="160"/>
   <Column ss:Width="130"/>
   <Column ss:Width="80"/>`;

      for (let d = 1; d <= daysInMonth; d++) {
        xml += `<Column ss:Width="32"/>`;
      }
      xml += `<Column ss:Width="85"/>`;

      xml += `
   <Row ss:Height="26">
    <Cell ss:MergeAcross="${daysInMonth + 4}" ss:StyleID="TitleStyle">
     <Data ss:Type="String">ТАБЕЛЬ УЧЕТА РАБОЧЕГО ВРЕМЕНИ ЗА ${currentMonthName.toUpperCase()} ${currentYear} Г.</Data>
    </Cell>
   </Row>
   <Row ss:Height="12"></Row>`;

      xml += `
   <Row ss:Height="25">
    <Cell ss:StyleID="HeaderCol"><Data ss:Type="String">№</Data></Cell>
    <Cell ss:StyleID="HeaderCol"><Data ss:Type="String">ФИО Исполнителя</Data></Cell>
    <Cell ss:StyleID="HeaderCol"><Data ss:Type="String">Специальность</Data></Cell>
    <Cell ss:StyleID="HeaderCol"><Data ss:Type="String">Показатель</Data></Cell>`;

      for (let d = 1; d <= daysInMonth; d++) {
        const dateObj = new Date(currentYear, currentMonth - 1, d);
        const isWeekend = dateObj.getDay() === 0 || dateObj.getDay() === 6;
        const style = isWeekend ? "HeaderColWeekend" : "HeaderCol";
        xml += `<Cell ss:StyleID="${style}"><Data ss:Type="Number">${d}</Data></Cell>`;
      }
      xml += `<Cell ss:StyleID="HeaderTotal"><Data ss:Type="String">ИТОГО</Data></Cell>
   </Row>`;

      visible.forEach((w, idx) => {
        const key = `${w.isForeman ? "f_" : "e_"}${w.id}`;
        const rate = Number(w.rate) || 0;
        let sumHours = 0;
        const daysShiftData = [];

        for (let d = 1; d <= daysInMonth; d++) {
          const ds = `${currentYear}-${String(currentMonth).padStart(2, "0")}-${String(d).padStart(2, "0")}`;
          const shift = shiftsDb[ds]?.[key];
          const h = shift ? Number(shift.totalHours || 0) : 0;
          const obj = shift && shift.object ? shift.object : "";
          const auth = shift && shift.author ? shift.author : "";
          if (h > 0) sumHours += h;
          daysShiftData.push({ day: d, hours: h, object: obj, author: auth });
        }

        const totalEarn = Math.round(sumHours * rate);

        xml += `
   <Row ss:Height="20">
    <Cell ss:MergeDown="3" ss:StyleID="CellMetric"><Data ss:Type="Number">${idx + 1}</Data></Cell>
    <Cell ss:MergeDown="3" ss:StyleID="CellFio"><Data ss:Type="String">${escapeXml(w.name)}</Data></Cell>
    <Cell ss:MergeDown="3" ss:StyleID="CellRole"><Data ss:Type="String">${escapeXml(w.role)}</Data></Cell>
    <Cell ss:StyleID="CellMetric"><Data ss:Type="String">Часы</Data></Cell>`;

        daysShiftData.forEach(item => {
          const dateObj = new Date(currentYear, currentMonth - 1, item.day);
          const isWeekend = dateObj.getDay() === 0 || dateObj.getDay() === 6;
          const style = isWeekend ? "CellHoursWeekend" : "CellHours";
          if (item.hours > 0) {
            xml += `<Cell ss:StyleID="${style}"><Data ss:Type="Number">${item.hours}</Data></Cell>`;
          } else {
            xml += `<Cell ss:StyleID="${style}"><Data ss:Type="String"></Data></Cell>`;
          }
        });
        xml += `<Cell ss:StyleID="CellTotalHours"><Data ss:Type="Number">${+sumHours.toFixed(2)}</Data></Cell>
   </Row>`;

        xml += `
   <Row ss:Height="18">
    <Cell ss:Index="4" ss:StyleID="CellMetric"><Data ss:Type="String">Объект</Data></Cell>`;
        daysShiftData.forEach(item => {
          const shortObj = item.object ? item.object.substring(0, 5) : "";
          xml += `<Cell ss:StyleID="CellObj"><Data ss:Type="String">${escapeXml(shortObj)}</Data></Cell>`;
        });
        xml += `<Cell ss:StyleID="CellObj"><Data ss:Type="String">—</Data></Cell>
   </Row>`;

        xml += `
   <Row ss:Height="18">
    <Cell ss:Index="4" ss:StyleID="CellMetric"><Data ss:Type="String">Ответств.</Data></Cell>`;
        daysShiftData.forEach(item => {
          const shortAuthor = item.author ? (item.author.split(" ")[0] || item.author).substring(0, 7) : "";
          xml += `<Cell ss:StyleID="CellObj"><Data ss:Type="String">${escapeXml(shortAuthor)}</Data></Cell>`;
        });
        xml += `<Cell ss:StyleID="CellObj"><Data ss:Type="String">—</Data></Cell>
   </Row>`;

        xml += `
   <Row ss:Height="20">
    <Cell ss:Index="4" ss:StyleID="CellMetric"><Data ss:Type="String">Сумма (₽)</Data></Cell>`;
        daysShiftData.forEach(item => {
          const sumDay = item.hours > 0 ? Math.round(item.hours * rate) : 0;
          if (sumDay > 0) {
            xml += `<Cell ss:StyleID="CellSum"><Data ss:Type="Number">${sumDay}</Data></Cell>`;
          } else {
            xml += `<Cell ss:StyleID="CellSum"><Data ss:Type="String"></Data></Cell>`;
          }
        });
        xml += `<Cell ss:StyleID="CellTotalMoney"><Data ss:Type="Number">${totalEarn}</Data></Cell>
   </Row>`;
      });

      xml += `
  </Table>
  <WorksheetOptions xmlns="urn:schemas-microsoft-com:office:excel">
   <PageSetup>
    <Layout x:Orientation="Landscape"/>
   </PageSetup>
   <FitToPage/>
   <Print>
    <ValidPrinterInfo/>
    <PaperSizeIndex>9</PaperSizeIndex>
    <HorizontalResolution>600</HorizontalResolution>
    <VerticalResolution>600</VerticalResolution>
   </Print>
   <Selected/>
   <FreezePanes/>
   <FrozenNoSplit/>
   <SplitPane>
    <TopRowBottomPane>3</TopRowBottomPane>
    <LeftColumnRightPane>4</LeftColumnRightPane>
    <ActivePane>0</ActivePane>
   </SplitPane>
  </WorksheetOptions>
 </Worksheet>
</Workbook>`;

      downloadExcelXml(xml, fileName);
    }

    function escapeXml(str) {
      if (!str) return "";
      return String(str)
        .replace(/&/g, "&amp;")
        .replace(/</g, "&lt;")
        .replace(/>/g, "&gt;")
        .replace(/"/g, "&quot;")
        .replace(/'/g, "&apos;");
    }

    function downloadExcelXml(content, filename) {
      const blob = new Blob([content], { type: "application/vnd.ms-excel;charset=utf-8;" });
      const url = URL.createObjectURL(blob);
      const a = document.createElement("a");
      a.href = url;
      a.download = filename;
      a.click();
    }

    function downloadCsv(content, filename) {
      const blob = new Blob(["\uFEFF" + content], { type: "text/csv;charset=utf-8;" });
      const url = URL.createObjectURL(blob);
      const a = document.createElement("a");
      a.href = url;
      a.download = filename;
      a.click();
    }

    /* ==============================================================
       АДМИНКА
       ============================================================== */
    function addNewForeman() {
      const name = document.getElementById("newForemanName").value.trim();
      const role = document.getElementById("newForemanRole").value.trim() || "Ответственный";
      const phone = document.getElementById("newForemanPhone").value.trim();
      const defObj = document.getElementById("newForemanObj").value.trim() || selectedObject;
      const rate = Number(document.getElementById("newForemanRate").value) || 750;
      const startTime = document.getElementById("newForemanStartTime").value || "08:00";

      if (!name) {
        showToast("Укажите ФИО ответственного");
        return;
      }

      const now = new Date();
      const newF = {
        id: Date.now(),
        name,
        role,
        phone,
        defaultObject: defObj,
        rate,
        startTime,
        startMonth: now.getMonth() + 1,
        startYear: now.getFullYear()
      };

      foremenList.push(newF);
      if (defObj && !objectsList.includes(defObj)) objectsList.push(defObj);

      document.getElementById("newForemanName").value = "";
      document.getElementById("newForemanPhone").value = "";
      document.getElementById("newForemanObj").value = "";

      saveState();
      pushStateToCloud();
      renderForemenRegistry();
      renderForemanWorkers();
      renderMatrixTable();
      showToast(`Ответственный ${name} добавлен`);
    }

    function renderForemenRegistry() {
      const container = document.getElementById("foremenRegistryList");
      if (!container) return;
      container.innerHTML = "";

      // Гарантируем корректный URL со слэшем перед параметрами (?foreman=...)
      let baseOrigin = (publicHostingDomain || "").trim().replace(/\/+$/, "");
      if (!baseOrigin || baseOrigin.includes("localhost") || baseOrigin.startsWith("file:")) {
        if (window.location.origin && !window.location.origin.includes("localhost") && !window.location.origin.startsWith("file:")) {
          baseOrigin = window.location.origin + window.location.pathname.replace(/\/+$/, "");
        } else {
          baseOrigin = "https://uchet-smen-tabel.vercel.app";
        }
      }

      foremenList.forEach(f => {
        // Обязательный слэш перед знаком вопроса, чтобы мобильные браузеры не выдавали ERR_CONNECTION
        const personalLink = `${baseOrigin}/?foreman=${f.id}`;
        const item = document.createElement("div");
        item.style = "background: #0f172a; border: 1px solid var(--border-color); border-radius: var(--radius-sm); padding: 10px 12px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 8px;";
        
        const badgeStyle = getRoleBadgeStyle(f.role);

        item.innerHTML = `
          <div>
            <div style="display: flex; align-items: center; gap: 6px; flex-wrap: wrap;">
              <span style="font-weight: 700; color: #38bdf8; font-size: 14px;">${f.name}</span>
              <span style="font-size: 11px; padding: 2px 7px; border-radius: 4px; ${badgeStyle}">${f.role || "Ответственный"}</span>
            </div>
            <div style="font-size: 12px; color: var(--text-muted); margin-top: 3px;">
              Телефон: ${f.phone || "—"} | Объект: ${f.defaultObject || "—"} | Старт: ${f.startTime || "08:00"} | Старт работы: ${f.startMonth || 11}.${f.startYear || 2026}
            </div>
            <div style="margin-top: 4px; display: flex; align-items: center; gap: 6px;">
              <span style="font-size: 12px; color: #cbd5e1;">Ставка:</span>
              <input type="number" value="${f.rate || 750}" style="width: 80px; padding: 2px 6px; font-size: 12px;" class="custom-input" onchange="updateForemanRate(${f.id}, this.value)">
              <span style="font-size: 12px; color: var(--text-muted);">₽/ч</span>
            </div>
          </div>
          <div style="display: flex; gap: 6px; align-items: center; flex-wrap: wrap;">
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #0284c7; color: #fff;" onclick="showForemanQrCode(${f.id})" title="Показать QR-код для сканирования камерой телефона">📲 QR-код</button>
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #3b82f6; color: #fff;" onclick="openEditForemanModal(${f.id})" title="Редактировать">✏️</button>
            <button class="action-btn" style="width: auto; padding: 6px 12px; font-size: 12px; background: #2563eb; color: #fff;" onclick="copyPersonalLink('${personalLink}')">📋 Скопировать ссылку</button>
            <button class="action-btn" style="width: auto; padding: 6px 10px; font-size: 12px; background: #dc2626; color: #fff;" onclick="deleteForeman(${f.id})">🗑️</button>
          </div>
        `;
        container.appendChild(item);
      });
    }

    function updateForemanRate(id, newRate) {
      const f = foremenList.find(x => x.id == id);
      if (f) {
        f.rate = Number(newRate) || 0;
        saveState();
        pushStateToCloud();
        renderMatrixTable();
        showToast("Ставка обновлена");
      }
    }

    function deleteForeman(id) {
      const f = foremenList.find(x => x.id === id);
      const name = f ? f.name : "ответственного";

      const step1 = window.confirm(`Очистить учётные данные ответственного: ${name}?`);
      if (!step1) return;

      const step2 = window.confirm(`Удалить ответственного: ${name} (переместить в архив)?`);
      if (!step2) return;

      if (f) {
        archivedWorkers.unshift({
          ...f,
          isForeman: true,
          archivedAt: new Date().toLocaleDateString("ru-RU") + " " + new Date().toLocaleTimeString("ru-RU", { hour: "2-digit", minute: "2-digit" })
        });
      }

      foremenList = foremenList.filter(x => x.id !== id);
      saveState();
      pushStateToCloud();
      renderForemenRegistry();
      renderArchivedWorkersTable();
      renderForemanWorkers();
      renderMatrixTable();
      showToast(`Ответственный "${name}" перемещён в архив`);
    }

    function openEditForemanModal(id) {
      const f = foremenList.find(x => x.id == id);
      if (!f) return;
      document.getElementById("editForemanIdInput").value = f.id;
      document.getElementById("editForemanNameInput").value = f.name;
      document.getElementById("editForemanRoleInput").value = f.role || "Ответственный";
      document.getElementById("editForemanPhoneInput").value = f.phone || "";
      document.getElementById("editForemanObjInput").value = f.defaultObject || "";
      document.getElementById("editForemanRateInput").value = f.rate || 750;
      document.getElementById("editForemanStartTimeInput").value = f.startTime || "08:00";
      document.getElementById("editForemanStartMonthInput").value = f.startMonth || 11;
      document.getElementById("editForemanStartYearInput").value = f.startYear || 2026;
      document.getElementById("editForemanModal").classList.add("open");
    }

    function closeForemanEditModal() {
      const m = document.getElementById("editForemanModal");
      if (m) m.classList.remove("open");
    }

    function saveForemanCardEdit() {
      const id = document.getElementById("editForemanIdInput").value;
      const f = foremenList.find(x => x.id == id);
      if (!f) return;

      f.name = document.getElementById("editForemanNameInput").value.trim();
      f.role = document.getElementById("editForemanRoleInput").value.trim();
      f.phone = document.getElementById("editForemanPhoneInput").value.trim();
      f.defaultObject = document.getElementById("editForemanObjInput").value.trim();
      f.rate = Number(document.getElementById("editForemanRateInput").value) || 0;
      f.startTime = document.getElementById("editForemanStartTimeInput").value || "08:00";
      f.startMonth = Number(document.getElementById("editForemanStartMonthInput").value) || 1;
      f.startYear = Number(document.getElementById("editForemanStartYearInput").value) || 2026;

      closeForemanEditModal();
      saveState();
      pushStateToCloud();
      renderForemenRegistry();
      renderForemanWorkers();
      renderMatrixTable();
      showToast("Карточка ответственного обновлена");
    }

    function openHostingHelpModal() {
      const m = document.getElementById("hostingHelpModal");
      if (m) m.classList.add("open");
    }

    function closeHostingHelpModal() {
      const m = document.getElementById("hostingHelpModal");
      if (m) m.classList.remove("open");
    }

    function saveCustomPublicDomain() {
      const inp = document.getElementById("customPublicDomainInput");
      if (!inp) return;
      let val = inp.value.trim();
      if (!val) {
        publicHostingDomain = "https://uchet-smen-tabel.vercel.app";
      } else {
        if (!val.startsWith("http://") && !val.startsWith("https://")) {
          val = "https://" + val;
        }
        publicHostingDomain = val.replace(/\/+$/, "");
      }
      saveState();
      renderForemenRegistry();
      showToast("Публичный домен сохранён! Ссылки и QR-коды обновлены.");
      closeHostingHelpModal();
    }

    function showForemanQrCode(foremanId) {
      const f = foremenList.find(x => x.id === foremanId);
      if (!f) return;

      let baseOrigin = (publicHostingDomain || "").trim().replace(/\/+$/, "");
      if (!baseOrigin || baseOrigin.includes("localhost") || baseOrigin.startsWith("file:")) {
        if (window.location.origin && !window.location.origin.includes("localhost") && !window.location.origin.startsWith("file:")) {
          baseOrigin = window.location.origin + window.location.pathname.replace(/\/+$/, "");
        } else {
          baseOrigin = "https://uchet-smen-tabel.vercel.app";
        }
      }

      const personalLink = `${baseOrigin}/?foreman=${f.id}`;
      activeQrLink = personalLink;

      document.getElementById("qrModalTitle").innerText = `Вход: ${f.name}`;
      document.getElementById("qrModalSubtitle").innerText = f.role || "Ответственный на объекте";
      document.getElementById("qrModalUrlText").innerText = personalLink;

      // Безопасная загрузка QR без зависания страницы
      const qrImg = document.getElementById("qrCodeImage");
      if (qrImg) {
        qrImg.src = `https://api.qrserver.com/v1/create-qr-code/?size=250x250&data=${encodeURIComponent(personalLink)}`;
      }

      document.getElementById("qrCodeModal").classList.add("open");
    }

    function closeQrModal() {
      const m = document.getElementById("qrCodeModal");
      if (m) m.classList.remove("open");
    }

    function copyQrLinkFromModal() {
      if (activeQrLink) {
        copyPersonalLink(activeQrLink);
      }
    }

    function copyPersonalLink(link) {
      let targetLink = link;
      if (!targetLink) {
        let base = (publicHostingDomain || "https://uchet-smen-tabel.vercel.app").trim().replace(/\/+$/, "");
        targetLink = `${base}/?foreman=1793895782377`;
      }
      const tempInp = document.createElement("input");
      tempInp.value = targetLink;
      document.body.appendChild(tempInp);
      tempInp.select();
      try {
        document.execCommand("copy");
        showToast("✓ Ссылка скопирована в буфер!");
      } catch (err) {
        showToast("Не удалось скопировать");
      }
      document.body.removeChild(tempInp);
    }

    function addNewEmployee() {
      const name = document.getElementById("newEmpName").value.trim();
      const role = document.getElementById("newEmpRole").value.trim() || "Самозанятый";
      const phone = document.getElementById("newEmpPhone").value.trim();
      
      const isSmzRole = role.toLowerCase().includes("самозанят") || role.toLowerCase().includes("разнораб") || role.toLowerCase().includes("подсоб");
      const defaultRate = isSmzRole ? 500 : 750;
      const rate = Number(document.getElementById("newEmpRate").value) || defaultRate;

      if (!name) {
        showToast("Укажите ФИО самозанятого");
        return;
      }

      const now = new Date();
      employees.push({
        id: Date.now(),
        name,
        role,
        phone,
        rate,
        startMonth: now.getMonth() + 1,
        startYear: now.getFullYear(),
        hiddenFromForemen: false
      });

      document.getElementById("newEmpName").value = "";
      document.getElementById("newEmpRole").value = "";
      document.getElementById("newEmpPhone").value = "";

      saveState();
      pushStateToCloud();
      renderRatesTable();
      renderForemanWorkers();
      renderMatrixTable();
      showToast(`Самозанятый ${name} добавлен`);
    }

    function renderRatesTable() {
      const tbody = document.getElementById("employeesRatesTableBody");
      const badge = document.getElementById("employeesCountBadge");
      const searchInp = document.getElementById("adminEmployeeSearchInput");
      if (!tbody) return;

      const q = searchInp ? searchInp.value.toLowerCase().trim() : "";
      const filtered = employees.filter(e => {
        if (!q) return true;
        return (
          e.name.toLowerCase().includes(q) ||
          (e.role && e.role.toLowerCase().includes(q)) ||
          (e.phone && e.phone.includes(q))
        );
      });

      if (badge) badge.innerText = `Всего: ${employees.length}`;
      tbody.innerHTML = "";

      if (filtered.length === 0) {
        tbody.innerHTML = `<tr><td colspan="8" style="padding: 16px; color: var(--text-muted);">Самозанятые не найдены</td></tr>`;
        return;
      }

      filtered.forEach((e, idx) => {
        const tr = document.createElement("tr");
        const isHidden = !!e.hiddenFromForemen;
        tr.innerHTML = `
          <td>${idx + 1}</td>
          <td style="text-align: left; font-weight: 700;">
            ${e.name}
            ${isHidden ? '<span style="font-size: 10px; color: #ef4444; margin-left: 6px; font-weight: normal;">(скрыт)</span>' : ''}
          </td>
          <td><span style="padding: 2px 6px; border-radius: 4px; font-size: 11px; ${getRoleBadgeStyle(e.role)}">${e.role}</span></td>
          <td>${e.phone || "—"}</td>
          <td>
            <input type="number" class="custom-input" value="${e.rate || 0}" style="width: 90px; padding: 4px 6px; text-align: center; margin: 0 auto;" onchange="updateEmployeeRateInline(${e.id}, this.value)">
          </td>
          <td>${e.startMonth || 11}.${e.startYear || 2026}</td>
          <td>
            <button class="action-btn" style="width: auto; padding: 4px 8px; font-size: 11px; background: ${isHidden ? '#334155' : '#059669'}; color: #fff;" onclick="toggleEmployeeVisibility(${e.id})">
              ${isHidden ? '👁️‍🗨️ Скрыт' : '👁️ Виден'}
            </button>
          </td>
          <td>
            <div style="display: flex; gap: 4px; justify-content: center;">
              <button class="action-btn" style="width: auto; padding: 4px 8px; font-size: 12px; background: #3b82f6;" onclick="openEditEmployeeModal(${e.id})">✏️</button>
              <button class="action-btn" style="width: auto; padding: 4px 8px; font-size: 12px; background: #dc2626;" onclick="deleteEmployee(${e.id})">🗑️</button>
            </div>
          </td>
        `;
        tbody.appendChild(tr);
      });
    }

    function toggleEmployeeVisibility(id) {
      const emp = employees.find(e => e.id == id);
      if (emp) {
        emp.hiddenFromForemen = !emp.hiddenFromForemen;
        saveState();
        pushStateToCloud();
        renderRatesTable();
        renderForemanWorkers();
        showToast(emp.hiddenFromForemen ? `Сотрудник "${emp.name}" скрыт` : `Сотрудник "${emp.name}" снова виден`);
      }
    }

    function updateEmployeeRateInline(id, newRate) {
      const emp = employees.find(e => e.id == id);
      if (emp) {
        emp.rate = Number(newRate) || 0;
        saveState();
        pushStateToCloud();
        renderMatrixTable();
        showToast("Ставка обновлена");
      }
    }

    function openEditEmployeeModal(id) {
      const emp = employees.find(e => e.id == id);
      if (!emp) return;
      document.getElementById("editEmpIdInput").value = emp.id;
      document.getElementById("editEmpNameInput").value = emp.name;
      document.getElementById("editEmpRoleInput").value = emp.role;
      document.getElementById("editEmpPhoneInput").value = emp.phone || "";
      document.getElementById("editEmpRateInput").value = emp.rate || 0;
      document.getElementById("editEmpStartMonthInput").value = emp.startMonth || 11;
      document.getElementById("editEmpStartYearInput").value = emp.startYear || 2026;
      document.getElementById("editEmployeeModal").classList.add("open");
    }

    function closeEmployeeEditModal() {
      const m = document.getElementById("editEmployeeModal");
      if (m) m.classList.remove("open");
    }

    function saveEmployeeCardEdit() {
      const id = document.getElementById("editEmpIdInput").value;
      const emp = employees.find(e => e.id == id);
      if (!emp) return;

      emp.name = document.getElementById("editEmpNameInput").value.trim();
      emp.role = document.getElementById("editEmpRoleInput").value.trim();
      emp.phone = document.getElementById("editEmpPhoneInput").value.trim();
      emp.rate = Number(document.getElementById("editEmpRateInput").value) || 0;
      emp.startMonth = Number(document.getElementById("editEmpStartMonthInput").value) || 1;
      emp.startYear = Number(document.getElementById("editEmpStartYearInput").value) || 2026;

      closeEmployeeEditModal();
      saveState();
      pushStateToCloud();
      renderRatesTable();
      renderForemanWorkers();
      renderMatrixTable();
      showToast("Карточка самозанятого обновлена");
    }

    function deleteEmployee(id) {
      const emp = employees.find(e => e.id === id);
      const name = emp ? emp.name : "сотрудника";

      const step1 = window.confirm(`Очистить учётные данные сотрудника: ${name}?`);
      if (!step1) return;

      const step2 = window.confirm(`Удалить сотрудника: ${name} (переместить в архив)?`);
      if (!step2) return;

      if (emp) {
        archivedWorkers.unshift({
          ...emp,
          isForeman: false,
          archivedAt: new Date().toLocaleDateString("ru-RU") + " " + new Date().toLocaleTimeString("ru-RU", { hour: "2-digit", minute: "2-digit" })
        });
      }

      employees = employees.filter(e => e.id !== id);
      saveState();
      pushStateToCloud();
      renderRatesTable();
      renderArchivedWorkersTable();
      renderForemanWorkers();
      renderMatrixTable();
      showToast(`Сотрудник "${name}" перемещён в архив`);
    }

    function renderArchivedWorkersTable() {
      const tbody = document.getElementById("archivedEmployeesTableBody");
      const badge = document.getElementById("archivedCountBadge");
      if (!tbody) return;

      if (badge) badge.innerText = `В архиве: ${archivedWorkers.length}`;
      tbody.innerHTML = "";

      if (archivedWorkers.length === 0) {
        tbody.innerHTML = `<tr><td colspan="8" style="padding: 16px; color: var(--text-muted);">Архив пуст</td></tr>`;
        return;
      }

      archivedWorkers.forEach((w, idx) => {
        const tr = document.createElement("tr");
        const categoryLabel = w.isForeman 
          ? `<span style="padding: 2px 6px; border-radius: 4px; font-size: 11px; background: rgba(168, 85, 247, 0.2); color: #c084fc; border: 1px solid #9333ea;">Ответственный</span>`
          : `<span style="padding: 2px 6px; border-radius: 4px; font-size: 11px; background: rgba(59, 130, 246, 0.2); color: #93c5fd; border: 1px solid #2563eb;">Самозанятый</span>`;

        tr.innerHTML = `
          <td>${idx + 1}</td>
          <td style="text-align: left; font-weight: 700; color: #cbd5e1;">${w.name}</td>
          <td><span style="padding: 2px 6px; border-radius: 4px; font-size: 11px; ${getRoleBadgeStyle(w.role)}">${w.role || "—"}</span></td>
          <td>${categoryLabel}</td>
          <td>${w.phone || "—"}</td>
          <td>${w.rate ? w.rate + " ₽/ч" : "—"}</td>
          <td style="font-size: 11px; color: #94a3b8;">${w.archivedAt || "—"}</td>
          <td>
            <button class="action-btn" style="width: auto; padding: 4px 10px; font-size: 11px; background: #059669; color: #fff; margin: 0 auto;" onclick="restoreWorkerFromArchive(${w.id}, ${!!w.isForeman})">
              ♻️ Восстановить
            </button>
          </td>
        `;
        tbody.appendChild(tr);
      });
    }

    function restoreWorkerFromArchive(id, isForeman) {
      const idx = archivedWorkers.findIndex(w => w.id === id && !!w.isForeman === isForeman);
      if (idx === -1) return;

      const worker = archivedWorkers.splice(idx, 1)[0];
      const { archivedAt, isForeman: _, ...cleanWorker } = worker;

      if (isForeman) {
        foremenList.push(cleanWorker);
        renderForemenRegistry();
      } else {
        employees.push(cleanWorker);
        renderRatesTable();
      }

      saveState();
      pushStateToCloud();
      renderArchivedWorkersTable();
      renderForemanWorkers();
      renderMatrixTable();
      showToast(`Сотрудник "${cleanWorker.name}" успешно восстановлен`);
    }

    /* ==============================================================
       БЭКАПЫ JSON
       ============================================================== */
    function exportFullJsonBackup() {
      const data = {
        employees,
        foremenList,
        archivedWorkers,
        objectsList,
        shiftsDb,
        universalDocs,
        exportDate: new Date().toISOString()
      };
      const blob = new Blob([JSON.stringify(data, null, 2)], { type: "application/json" });
      const url = URL.createObjectURL(blob);
      const a = document.createElement("a");
      a.href = url;
      a.download = `activity_hub_backup_${new Date().toISOString().slice(0,10)}.json`;
      a.click();
    }

    function importFullJsonBackup(event) {
      const file = event.target.files[0];
      if (!file) return;
      const reader = new FileReader();
      reader.onload = function(e) {
        try {
          const parsed = JSON.parse(e.target.result);
          if (parsed.employees) employees = parsed.employees;
          if (parsed.foremenList) foremenList = parsed.foremenList;
          if (parsed.archivedWorkers) archivedWorkers = parsed.archivedWorkers;
          if (parsed.objectsList) objectsList = parsed.objectsList;
          if (parsed.shiftsDb) shiftsDb = parsed.shiftsDb;
          if (parsed.universalDocs) universalDocs = parsed.universalDocs;
          saveState();
          location.reload();
        } catch (err) {
          showToast("Ошибка импорта файла");
        }
      };
      reader.readAsText(file);
    }

    function downloadThisHtmlFile() {
      const htmlContent = "<!DOCTYPE html>\n" + document.documentElement.outerHTML;
      const blob = new Blob([htmlContent], { type: "text/html;charset=utf-8;" });
      const url = URL.createObjectURL(blob);
      const a = document.createElement("a");
      a.href = url;
      a.download = "index.html";
      a.click();
    }

    /* ==============================================================
       ИНИЦИАЛИЗАЦИЯ
       ============================================================== */
    function startAppNow() {
      try {
        initPwaSupport();
        loadState();

        const now = new Date();
        currentYear = now.getFullYear();
        currentMonth = now.getMonth() + 1;
        const daysOfWeek = ["ВС", "ПН", "ВТ", "СР", "ЧТ", "ПТ", "СБ"];
        const monthsRu = ["Января", "Февраля", "Марта", "Апреля", "Мая", "Июня", "Июля", "Августа", "Сентября", "Октября", "Ноября", "Декабря"];
        const liveDate = document.getElementById("liveDateDisplay");
        if (liveDate) {
          liveDate.innerText = `${now.getDate()} ${monthsRu[now.getMonth()]} ${now.getFullYear()} (${daysOfWeek[now.getDay()]})`;
        }

        let foremanId = null;
        let isForemanMode = false;
        try {
          if (window.location.origin && !window.location.origin.includes("localhost") && !window.location.origin.startsWith("file:")) {
            publicHostingDomain = window.location.origin + window.location.pathname.replace(/\/+$/, "");
            safeSetItem("ah_public_domain", publicHostingDomain);
          }

          const rawSearch = window.location.search || "";
          const urlParams = new URLSearchParams(rawSearch);
          isForemanMode = urlParams.get("role") === "foreman";
          foremanId = urlParams.get("foreman");

          if (!foremanId && window.location.hash) {
            const hashParams = new URLSearchParams(window.location.hash.replace("#", "?"));
            foremanId = hashParams.get("foreman");
          }

          if (!foremanId) {
            const savedFid = safeGetItem("ah_saved_device_foreman_id");
            if (savedFid) {
              foremanId = savedFid;
              isForemanMode = true;
            }
          }
        } catch (e) {
          console.warn("URL parse fallback", e);
        }

        if (foremanId) {
          const fidStr = String(foremanId);
          currentForemanUser = foremenList.find(f => String(f.id) === fidStr) || {
            id: foremanId,
            name: "Петров Сергей",
            role: "Бригадир"
          };
          safeSetItem("ah_saved_device_foreman_id", fidStr);
        }

        if (isForemanMode || currentForemanUser) {
          const btnRates = document.getElementById("tabBtnRates");
          const btnMatrix = document.getElementById("tabBtnMatrix");
          const downloadBtn = document.getElementById("btnDownloadHtml");
          const exportCsvBtn = document.getElementById("btnExportCsv");

          if (btnRates) btnRates.style.display = "none";
          if (btnMatrix) btnMatrix.style.display = "none";
          if (downloadBtn) downloadBtn.style.display = "none";
          if (exportCsvBtn) exportCsvBtn.style.display = "none";

          switchTab("foreman");

          if (currentForemanUser) {
            const nameDisp = document.getElementById("currentForemanDisplay");
            if (nameDisp) nameDisp.innerText = currentForemanUser.name;
            if (currentForemanUser.defaultObject) {
              selectedObject = currentForemanUser.defaultObject;
              if (!objectsList.includes(selectedObject)) {
                objectsList.push(selectedObject);
              }
            }
          }
        } else {
          renderForemenRegistry();
        }

        const timeInp = document.getElementById("declaredTimeInput");
        if (timeInp) timeInp.value = getCurrentTimeStr();

        renderObjectsSelect();
        renderForemanWorkers();
        renderRatesTable();
        renderArchivedWorkersTable();
        renderMatrixTable();
        renderUniversalDocsTable();
        initLiveTimersLoop();

        // Запуск облачных модулей строго в фоне через 2 секунды после полной отрисовки
        setTimeout(() => {
          initGpsTracking();
          initCloudSync();
        }, 2000);
      } catch (criticalErr) {
        console.error("Critical start error:", criticalErr);
      }
    }

    if (document.readyState === "loading") {
      document.addEventListener("DOMContentLoaded", startAppNow);
    } else {
      startAppNow();
    }
  </script>

</body></html>
