# bilibili-stream-crack

```js
const origFetch = unsafeWindow.fetch;
unsafeWindow.fetch = async (resource, config) => {
  let response = await origFetch(resource, config);
  if (typeof resource === "string" && resource.search(/\/get(H5)?InfoByRoom\?/) > 0) {
      const json = () => response.clone().json().then((data) => {
        if (data?.data?.block_info?.block) {
          data.data.block_info.block = false;
        }
        return data;
      });
      response.json = json;
  }
  return response;
};
 
try {
  let desc = Object.getOwnPropertyDescriptor(unsafeWindow, "__NEPTUNE_IS_MY_WAIFU__");
  let getter, setter;
  if (desc != undefined) {
    getter = desc.get;
    setter = desc.set;
  }
  let value;
  Object.defineProperty(unsafeWindow, "__NEPTUNE_IS_MY_WAIFU__", {
    enumerable: true,
    get: () => {
      if (getter != undefined) {
        let v = getter();
        if (v?.roomInfoRes?.data?.block_info?.block) {
          v.roomInfoRes.data.block_info.block = false;
        }
        return v;
      } else {
        return value;
      }
    },
    set: (v) => {
      value = v;
      if (value?.roomInfoRes?.data?.block_info?.block) {
        value.roomInfoRes.data.block_info.block = false;
      }
      if (setter != undefined) {
        setter(value);
      }
    }
  });
} catch(ex) {
  if (/^\/[0-9]+/.test(location.pathname)) {
    location.pathname = "/blanc" + location.pathname;
  }
}
 
})();
```