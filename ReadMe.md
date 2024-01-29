# لإخفاء عناصر معينة داخل القائمة باستخدام المراقب MutationObserver

```
  var targetNode = document.querySelector('.btn-group');

        var observer = new MutationObserver(function (mutations) {
            mutations.forEach(function (mutation) {
                var isDropdownOpen = targetNode.querySelector('.dropdown-menu').classList.contains('show');

                if (isDropdownOpen) {
                    // قم بتنفيذ الأكواد الخاصة بك هنا عندما يتم فتح القائمة
                    console.log('القائمة مفتوحة');
                    var archiveItem = Array.from(targetNode.querySelectorAll('.dropdown-menu a')).find(function (item) {
                        return item.textContent.trim() === 'ارشيف';
                    });
                    if (archiveItem) { archiveItem.style.display = 'none'; }

                    var delItem = Array.from(targetNode.querySelectorAll('.dropdown-menu a')).find(function (item) {
                        return item.textContent.trim() === 'حذف';
                    });
                    if (delItem) { delItem.style.display = 'none'; }


                } else {
                    // قم بتنفيذ الأكواد الخاصة بك هنا عندما يتم إغلاق القائمة
                    console.log('القائمة مغلقة');
                }
            });
        });

        var config = { attributes: true, childList: true, subtree: true };

        observer.observe(targetNode, config);
    
```