Django Hybrid Storage
====================

Use multiple file storages to serve and store file.

This project is based on work by Andrew Ingram. Thanks Andrew!


## Installation

    pip install django-hybridstorage

## Usage

Update your `settings.py`:

```python
DEFAULT_FILE_STORAGE = 'hybridstorage.storages.HybridStorage'
HYBRID_STORAGE_BACKENDS = (
    'django.core.files.storage.FileSystemStorage',
    'my_project.s3utils.MediaRootS3BotoStorage',
)
```

In this example `MediaRootS3BotoStorage` is derivered from `django-storages`'s `storages.backends.s3boto.S3BotoStorage` class. See http://stackoverflow.com/a/10825691

Hybridstorage iterates `HYBRID_STORAGE_BACKENDS` until desired IO operation completes successfully.

**Note:** File removal operation is disabled to prevent accidental deletions!


License
=======

Copyright © Tomi Pajunen

All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

* Redistributions of source code must retain the above copyright notice, this
  list of conditions and the following disclaimer.

* Redistributions in binary form must reproduce the above copyright notice,
  this list of conditions and the following disclaimer in the documentation
  and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
