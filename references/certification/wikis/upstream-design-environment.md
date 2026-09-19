# Environment

**URL:** [https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/Environment](https://gitlab.com/raidiam-conformance/open-finance/certification/-/wikis/UpStream-Design/Environment)
**Slug:** `UpStream-Design/Environment`

---

The **Environment** holds the state of a currently running [`TestModule`](./TestModule) as it executes, allowing the [`Condition`](./Condition)s in the test to pass values to each other as they execute in succession. 

Values in the **Environment** are stored as `JsonObject`s, indexed by a `String` object identifier. The `JsonObject` is stored and accessed by reference, so once it is stored in the **Environment** it should not be manipulated directly.

Arbitrary `JsonObject`s can be stored at a location key by calling `put(key, obj)`. A `JsonObject` can be fetched by calling `get(key)`. 

Members of a `JsonObject` can be accessed by calling `getString(key, path)`, `getInteger(key, path)`, `getBoolean(key, path)`, where `key` is the object's identifier and `path` is the constructed location of the desired field within the object. To construct the path, concatenate the member names of every containing object, in order, separated by the `.` character. 

For example, given an object with the construction:

```json

{
 "foo": { 
   "bar": { 
     "baz": "value" 
   } 
 } 
}
```

The string value is accessible using the path `foo.bar.baz`. If this object is stored under the key `demo`, the call to get the stored value would be `getString("demo", "foo.bar.baz")`. This same construct can be used to retrieve an arbitrary `JsonElement` with the `getElementFromObject(key, path)` method, without any type checking or coercion.

Any element that is not of the appropriate type will throw an `InvalidArgumentException`. For example, if a value is stored as the string `"1234"` and the `getInteger(key, path)` function is used to access it, the exception will be thrown.

There is also a utility function to determine whether the **Environment** contains an object stored under the given ID with `containsObject(key)`. 

## Native Values

Single native values (such as strings, integers, longs, and booleans) can be stored in the **Environment** by calling `putString(key)` / `putInteger(key)` / `putBoolean(key)` / `putLong(key)`, and retrieved by calling `getString(key)` / `getInteger(key)` / `getBoolean(key)` / `getLong(key)`. These are stored in a special section of the **Environment** internally (as a separate object containing only single values instead of objects).

## Mapping

Keys in the **Environment** can be mapped over each other using `mapKey(from, to)`, hiding the key that has been mapped over. This can be used to point part of the **Environment** to a different object for either access or writing. The original object will remain untouched while its key is mapped, and access will be restored once the key is unmapped with `unmapKey(key)`. 

For example, if the store originally looks like:

```json
{
    foo: { bar: 1234 },
    baz: { qux: 9876 }
}
```

Calls to `getObject(foo)` will return `{ bar : 1234 }`

If the key `baz` is mapped over the key `foo` with `mapKey("foo", "baz")`, this points all references to the key `foo` to use the existing "baz" object the store effectively looks like:

```json
{
    <hidden foo>: { bar: 1234 },
    foo <mapped over baz>: { qux: 9876 }
}
```

Any calls to object functions using `foo` such as `getObject(foo)` will return `{ qux: 9876 }`. Any calls to objects functions using `baz` will still access the original object for `baz`, such as `getObject(baz)` will return `{ qux: 9876 }`.


---

*Conteúdo baixado em 16/09/2026, 15:38:42*
