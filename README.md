# tag_autocomplete_helper 수정본


File "", line 850, in exec_module
  File "", line 228, in _call_with_frames_removed
  File "/content/drive/MyDrive/SD/extensions/a1111-sd-webui-tagcomplete/scripts/tag_autocomplete_helper.py", line 198, in 
    write_tag_base_path()
  File "/content/drive/MyDrive/SD/extensions/a1111-sd-webui-tagcomplete/scripts/tag_autocomplete_helper.py", line 173, in write_tag_base_path
    f.write(TAGS_PATH.relative_to(FILE_DIR).as_posix())
  File "/usr/lib/python3.9/pathlib.py", line 939, in relative_to
    raise ValueError("{!r} is not in the subpath of {!r}"
ValueError: '/content/drive/MyDrive/SD/extensions/a1111-sd-webui-tagcomplete/tags' is not in the subpath of '/content/repository' OR one path is relative and the other is absolute.

오류가 떠서


def write_tag_base_path():
    tags_path = Path("/content/drive/MyDrive/SD/extensions/a1111-sd-webui-tagcomplete/tags")
    file_dir = Path(__file__).resolve().parent.parent
    base_path = tags_path.resolve().relative_to(file_dir.resolve())
    with open(TAG_BASE_PATH_FILE, "w") as f:
        f.write(base_path.as_posix())
       
함수 추가하고
태그 기본 경로에
TAG_BASE_PATH_FILE = "/content/drive/MyDrive/SD/extensions/a1111-sd-webui-tagcomplete/scripts/tag_base_path.txt"
변수정의함


오류는 사라졌지만 자동완성 기능이 안됨.
