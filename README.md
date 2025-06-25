
## 🚀 Установка:
1. Скачай и распакуй мод в `mods/` Minetest.
2. Включи мод в настройках мира.
3. Получи радио командой или через крафт.

## 🎵 Добавление своих треков:
Просто замени файлы в `sounds/` на свои `.ogg`:
- `music1.ogg`
- `music2.ogg`
- `music3.ogg`

## 🖼 Текстуры:
Ты можешь заменить `radio_top.png` и `radio_side.png` в папке `textures/`.

---

Автор: DimaPuZ  
Лицензия: MIT
"""

license_content = """
MIT License

Copyright (c) 2025 DimaPuZ

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
"""

# Сохраняем эти файлы
with open(f"{mod_name}/README.md", "w", encoding="utf-8") as f:
    f.write(readme_content.strip())

with open(f"{mod_name}/LICENSE", "w", encoding="utf-8") as f:
    f.write(license_content.strip())

# Пересоздаем архив со всеми обновлёнными файлами
zip_final = "/mnt/data/real_radio_final_with_docs.zip"
with ZipFile(zip_final, 'w') as zipf:
    for foldername, subfolders, filenames in os.walk(mod_name):
        for filename in filenames:
            filepath = os.path.join(foldername, filename)
            zipf.write(filepath, arcname=os.path.relpath(filepath, mod_name))

zip_final
