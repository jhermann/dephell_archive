# DepHell Archive

Module to work with files and directories in archive in [pathlib](https://docs.python.org/3/library/pathlib.html) style.

* **Goal:** provide the same interface as `pathlib.Path` for archives.
* **State:** partially implemented. Need to implement more methods.

## Usage

```python
from pathlib import Path
from tempfile import TemporaryDirectory

from dephell_archive import ArchivePath

with TemporaryDirectory() as cache:
  path = ArchivePath(
    archive_path=Path('tests', 'requirements', 'wheel.whl'),
    cache_path=Path(cache),
  )
  subpath = path / 'dephell' / '__init__.py'
  with subpath.open() as stream:
    content = stream.read()
```