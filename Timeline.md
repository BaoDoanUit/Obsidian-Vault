---
tags: [timeline, test]
---

- Tag <<<
-  Event Info Block


<span 
	  class='ob-timelines' 
	  data-date='2000-10-10-00' 
	  data-title='Another Event' 
	  data-class='orange' 
	  data-img = 'Images/Pasted image 20221023105027.png' 
	  data-type='range' 
	  data-end='2000-10-20-00'> 
	A second event!
</span>

<span class='ob-timelines' data-date='1499-03-28-00' data-title="An example"></span>



```css
/* Render the ob-timelines span or div elements as inline blocks that use an italic font */
.ob-timelines {
  display: inline-block !important;
  font-style: italic;
}
/* Use the before pseudo element to display attributes of the span or div */
.ob-timelines::before {
  content: "🔖 " attr(data-date) ": " attr(data-title) ". ";
  color: lilac;
  font-weight: 500;
}
```