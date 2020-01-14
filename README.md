lager_iowrite_formatter
=====

![GitHub Workflow Status](https://img.shields.io/github/workflow/status/kobil-systems/lager_iowrite_formatter/Erlang%20CI?style=flat-square)

Lager formatter that adds support for custom format specifiers to the metadata.
It is especially useful when you want to format numbers in different format.

Usage
-----

Add to `rebar.config`:

```erlang
{deps, [lager_iowrite_formatter]}.
```

And then in `sys.config` you can use:

```erlang
{lager, [
  {handlers, [
    {lager_file_backend, [{file, "error.log"}, {level, error}, {formatter, lager_iowrite_formatter},
      {formatter_config, [date, " ", time, {"~.16B", trace_id, "undefined"}," [",severity,"] ",pid, " ", message, "\n"]}]}
  ]}
]}.
```

That will print `trace_id` metadata attribute using hexadecimal format if value
is present.
