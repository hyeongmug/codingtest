## PaginationHelper
https://www.codewars.com/kata/515bb423de843ea99400000a

### 문제
For this exercise you will be strengthening your page-fu mastery. You will complete the PaginationHelper class, which is a utility class helpful for querying paging information related to an array.

The class is designed to take in an array of values and an integer indicating how many items will be allowed per each page. The types of values contained within the collection/array are not relevant.

The following are some examples of how this class is used:
```
var helper = new PaginationHelper(['a','b','c','d','e','f'], 4);
helper.pageCount(); //should == 2
helper.itemCount(); //should == 6
helper.pageItemCount(0); //should == 4
helper.pageItemCount(1); // last page - should == 2
helper.pageItemCount(2); // should == -1 since the page is invalid

// pageIndex takes an item index and returns the page that it belongs on
helper.pageIndex(5); //should == 1 (zero based index)
helper.pageIndex(2); //should == 0
helper.pageIndex(20); //should == -1
helper.pageIndex(-10); //should == -1
```

### 해답
#### 내가 짠 코드
```javascript
function PaginationHelper(collection, itemsPerPage){
  this.collection = collection;
  this.itemsPerPage = itemsPerPage;
}

PaginationHelper.prototype.itemCount = function() {
  return this.collection.length;
}

PaginationHelper.prototype.pageCount = function() {
  return Math.ceil(this.itemCount() / this.itemsPerPage);
}

PaginationHelper.prototype.pageItemCount = function(pageIndex) {
  if (pageIndex + 1 == this.pageCount()) {
    return this.itemCount() % this.itemsPerPage;
  }
  if (pageIndex + 1 > this.pageCount() || 0 > pageIndex) {
    return -1;
  }
  return this.itemsPerPage;
}

PaginationHelper.prototype.pageIndex = function(itemIndex) {
  if (this.itemCount() < itemIndex + 1 || itemIndex < 0) {
    return -1;
  }
  return Math.ceil((itemIndex + 1) / this.itemsPerPage) - 1;
}
```

#### 다른사람이 짠 코드
```javascript
function PaginationHelper(collection, itemsPerPage){
  this.collection = collection, this.itemsPerPage = itemsPerPage;
}

PaginationHelper.prototype.itemCount = function() {
  return this.collection.length;
}

PaginationHelper.prototype.pageCount = function() {
  return Math.ceil(this.collection.length / this.itemsPerPage);
}

PaginationHelper.prototype.pageItemCount = function(pageIndex) {
  return pageIndex < this.pageCount()
          ? Math.min(this.itemsPerPage, this.collection.length - pageIndex * this.itemsPerPage)
          : -1;
}

PaginationHelper.prototype.pageIndex = function(itemIndex) {
  return itemIndex < this.collection.length && itemIndex >= 0
          ? Math.floor(itemIndex / this.itemsPerPage)
          : -1;
}
```


나도 나름 괜찮게 짠 것 같다(?)

근데 다른 사람들 코드 보면 1부터 시작하는 count 와 0부터 시작하는 index 가 있으면 이 둘의 비교가 필요할 때 index에 +1 하는 나와는 달리, count에 -1 해서 비교하는게 많은데 사고방식의 차이인지 아니면 그렇게 해야하는 이유가 있는지 궁금하다.