# django html pagination snippet

!! I will refactor these, I hope I don't forget ;)

~~~html
<style>
    .page-side-btn {
        background-color: #ca995e;
        border-color: #a07d53;
        transition: background-color 0.3s;
    }
    .page-side-btn:hover {
        background-color: #866b4b;
    }
    
    .page-numbers-btn {
        background-color: #ffffff00;
        border-color: #92744f;
        transition: background-color 0.3s;
    }
    .page-numbers-btn:hover {
        background-color: #ca995e;
    }

    .page-selected-btn {
        background-color: #ca995e;
        border-color: #a07d53;
    }
</style>
~~~

~~~html
<!-- pagination -->
<div class="text-center">
    {% if page_obj.has_previous %}
        <a href="?sayfa=1" class="btn page-side-btn">İlk</a>
        <a href="?sayfa={{ page_obj.previous_page_number }}" class="btn page-side-btn">Önceki</a>
    {% endif %}

    {% for a in page_obj.paginator.page_range %}
        {% if a == page_obj.number %}
            <div class="btn page-selected-btn">{{ a }}</div>
        {% elif a < page_obj.number|add:"5"  and a > page_obj.number|add:"-5" %}
            <a href="?sayfa={{ a }}" class="btn page-numbers-btn">{{ a }}</a>
        {% endif %}        
    {% endfor %}

    {% if page_obj.has_next %}
        <a href="?sayfa={{ page_obj.next_page_number }}" class="btn page-side-btn">Sonraki</a>
        <a href="?sayfa={{ page_obj.paginator.num_pages }}" class="btn page-side-btn">Son</a>
    {% endif %}
</div>
~~~
