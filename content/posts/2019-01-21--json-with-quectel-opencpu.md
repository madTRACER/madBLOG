---
title: 'JSON with Quectel OpenCPU'
description: 'When anybody talks about JSON, we remind about it’s usage in Web programming, client – server and server – server data transmission. However, we can use this form of data in embedded devices. I want to show my experience in usage JSON in programming of Quectel modules with OpenCPU.'
date: '2019-01-21T22:33:40+06:00'
template: 'post'
draft: false
slug: 'json-with-quectel-opencpu'
category: 'Wireless'
tags: ['C', 'C++' ,'Quectel', 'OpenCPU', 'GSM', 'Wireless']
socialImage: '/media/2019-01-21--json-opencpu.png'
---
![](/media/2019-01-21--json-opencpu.png)

*My friend wrote this* [*post*](https://blog.radiotech.kz/gsm-gps/ispolzuem-json-v-quectel-opencpu/) *in Russian and I couldn’t find any information about it, so I want to translate it for you.*

When anybody talks about JSON, we remind about it’s usage in Web programming, client – server and server – server data transmission. However, we can use this form of data in embedded devices. I want to show my experience in usage JSON in programming of Quectel modules with OpenCPU.

First of all, a small quote from Wikipedia about JSON:

> In [computing](https://en.wikipedia.org/wiki/Computing), **JavaScript Object Notation** (**JSON**) ([/ˈdʒeɪsən/](https://en.wikipedia.org/wiki/Help:IPA/English) “jay-son”, [/dʒeɪˈsɒn/](https://en.wikipedia.org/wiki/Help:IPA/English)) is an [open-standard](https://en.wikipedia.org/wiki/Open_standard) [file format](https://en.wikipedia.org/wiki/File_format) that uses [human-readable](https://en.wikipedia.org/wiki/Human-readable_medium) text to transmit data objects consisting of [attribute–value pairs](https://en.wikipedia.org/wiki/Attribute%E2%80%93value_pair) and [array data types](https://en.wikipedia.org/wiki/Array_data_type) (or any other [serializable](https://en.wikipedia.org/wiki/Serialization) value). It is a very common [data](https://en.wikipedia.org/wiki/Data) format used for [asynchronous](https://en.wikipedia.org/wiki/Asynchronous_I/O) browser–server communication, including as a replacement for [XML](https://en.wikipedia.org/wiki/XML) in some [AJAX](https://en.wikipedia.org/wiki/Ajax_(programming))-style systems.

OpenCPU is written in C so we cannot use different C++ libraries with JSON dependencies. Moreover, the resources are limited, because it is not a personal computer :). For instance, in Quectel M66 we have 360 kB Flash and 100kB RAM.

Speaking of which, OpenCPU is not so user-friendly, and while using it, you can often face with questions, which were never discussed. The library is replete with binaries and it’s sometimes hard to understand how function works. However, we have no other choice, so we need to use what we have.

Based on the above, I was trying to find a code to use JSON according to this criteria:

1. It should have no dependencies;
2. It must be written in C;
3. It must be useful for my needs;
4. It should have ability to form JSON objects and serialize them.

I found [JFES](https://github.com/NeonMercury/jfes) – JSON For Embedded Systems. Documentation of the project is written it README of the repo. I hope you read it, so let’s move to the usage of it with OpenCPU.

In order to start working with JFES you need to copy files *jfes.c* and *jfes.h* to the **/custom** folder of OpenCPU project and include header file in *main.c* :

```c
    #include "jfes.h"
```

Then you need to initialize *jfes\_config\_t* object:

```c
    jfes_config_t config;
```

JFES doesn’t support automatic memory allocation, so you need to use memory allocating functions by OpenCPU:

```c
    config.jfes_malloc = Ql_MEM_Alloc;
    config.jfes_free = Ql_MEM_Free;
```

After the end of initializing we can parse JSON. Let’s try a sample to form the JSON to send it by GPRS:

```json
    {
        "id": 12345,
        "imei": "759304218643261",
        "status": true
    }
```

The piece of code will look like this:

```c
    jfes_value_t data;
    jfes_value_t * value = jfes_create_object_value ( &config );
    jfes_set_object_property ( &config, value, jfes_create_integer_value ( &config, 12345 ), "id", 0 );
    jfes_set_object_property ( &config, value, jfes_create_string_value ( &config, "759304218643261", 0 ), "imei", 0 );
    jfes_set_object_property ( &config, value, jfes_create_boolean_value ( &config, true ), "status", 0 );
    jfes_set_object_property ( &config, &data, jfes_create_null_value ( &config ), "null_property", 0 );
```

When you create string-type object you need to send the length of the string (or 0 if string is ended by null symbol) as the last parameter.

Then we are serializing the object to the string before sending. The length of the string will be stored in *dump\_size* variable:

```c
    char beauty_dump[1024];
    jfes_size_t dump_size = 1024;
    jfes_value_to_string ( &data, &beauty_dump[0], &dump_size, 1 );
```

If you send 1 instead of 0 as the last parameter, then created string will be without spaces, tabs, carries etc. *(ugly JSON).*

The produced string won’t be null-terminated, so null must be added to the end:

```c
    beauty_dump[dump_size] = '\0';
```

The produced JSON can be outputted to the debugging interface:

```c
    APP_DEBUG ( "[ JSON ] %s \r\n",  &beauty_dump[0] );
```

That is what I wanted to tell you about. I hope this information was useful for you…