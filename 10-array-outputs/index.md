---
teaching: 10
exercises: 0
questions:
- "What do I do when a tool produces output in more than one file?"
- "How do I specify which output files should be kept?"
objectives:
- "Learn how to create arrays of output files."
keypoints:
- "You can capture multiple output files into an array of files using `glob`."
- "Use wildcards and filenames to specify the output files that will be returned
after tool execution."
---

# Array Outputs

You can also capture multiple output files into an array of files using `glob`.

*array-outputs.cwl*

```{literalinclude} /_includes/cwl/10-array-outputs/array-outputs.cwl
:language: yaml
```

*array-outputs-job.yml*

```{literalinclude} /_includes/cwl/10-array-outputs/array-outputs-job.yml
:language: yaml
```

Now invoke `cwl-runner` providing the tool wrapper and the input object
on the command line:

~~~
$ cwl-runner array-outputs.cwl array-outputs-job.yml
[job 140190876078160] /home/example$ touch foo.txt bar.dat baz.txt
Final process status is success
{
  "output": [
    {
      "size": 0,
      "location": "foo.txt",
      "checksum": "sha1$da39a3ee5e6b4b0d3255bfef95601890afd80709",
      "class": "File"
    },
    {
      "size": 0,
      "location": "baz.txt",
      "checksum": "sha1$da39a3ee5e6b4b0d3255bfef95601890afd80709",
      "class": "File"
    }
  ]
}
~~~

As described in the [YAML Guide](../yaml/index.md#arrays),
the array of expected outputs is specified in `array-outputs-job.yml` with each
entry marked by a leading `-`. This format can also be used in CWL descriptions
to mark entries in arrays, as demonstrated in several of the upcoming sections.

```{include} ../_includes/links.md
```