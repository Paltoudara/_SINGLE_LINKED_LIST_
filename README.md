# 🔗 Welcome to the _SINGLE_LINKED_LIST_ API 🌐:
# 🧩 Interface:
```markdown
```cpp
template<typename _Ty>
class single_linked_list final {
public:
	using iterator = list_node_iterator<true>;
	using const_iterator = list_node_iterator <false>;

	single_linked_list()noexcept;

	single_linked_list(const std::initializer_list<_Ty>& other);

	~single_linked_list()noexcept;

	single_linked_list(const single_linked_list<_Ty>& other);

	single_linked_list(single_linked_list<_Ty>&& other)noexcept;

	single_linked_list<_Ty>& operator =(const single_linked_list<_Ty>& other)&;

	single_linked_list<_Ty>& operator =(single_linked_list<_Ty>&& other) & noexcept;

	single_linked_list<_Ty>& operator=(const std::initializer_list<_Ty>& other)&;

	bool is_ascending()const;

	template<typename Compare>
	bool is_ascending(Compare comp)const;

	bool is_descending()const;

	template<typename Compare>
	bool is_descending(Compare comp)const;

	bool is_sorted()const;

	template<typename Compare1, typename Compare2 >
	bool is_sorted(Compare1 comp1, Compare2 comp2)const;
	
	bool push_back(const _Ty& data);

	bool push_back(_Ty&& data);

	template<class ..._Valty>
	bool emplace_back(_Valty&&..._Val);

	template<class ..._Valty>
	bool emplace_front(_Valty&&..._Val);

	bool push_front(const _Ty& data);

	bool push_front(_Ty&& data);

	void pop_front();

	void pop_back();

	void reverse()noexcept;

	bool insert_after(const_iterator pos, const _Ty& data);

	bool add_unique_after(const_iterator pos, const _Ty& data);

	template<typename _Pred1>
	bool add_unique_after(const_iterator pos, const _Ty& data, _Pred1 _Pred);

	void unique();

	template<typename _Pred1>
	void unique(_Pred1 _Pred);

	void show()const;

	void remove(const _Ty& val);

	template<typename _Pred1>
	void remove_if(_Pred1 _Pred);

	void merge(single_linked_list<_Ty>& other);

	void merge(single_linked_list<_Ty>&& other);

	template<typename Compare>
	void merge(single_linked_list<_Ty>& other, Compare comp);

	template<typename Compare>
	void merge(single_linked_list<_Ty>&& other, Compare comp);

	bool erase_after(const_iterator pos);

	bool empty()const noexcept;

	std::size_t size()const noexcept ;

	void swap(single_linked_list<_Ty>& other)noexcept;

	_NODISCARD _Ty&& back()&& ;


	_NODISCARD const _Ty&& back()const&& ;

	_NODISCARD const _Ty& back()const& ;
	_NODISCARD _Ty& back()& ;

	_NODISCARD const _Ty& front()const&;

	_NODISCARD _Ty& front()& ;

	_NODISCARD _Ty&& front()&&;

	_NODISCARD const _Ty&& front()const&& ;

	const_iterator begin()const noexcept ;

	iterator begin()noexcept;

	const_iterator end()const noexcept ;

	iterator end() noexcept ;
	const_iterator cbegin()const noexcept ;

	const_iterator cend()const noexcept ;

	bool unsafe_insert(const_iterator pos, const _Ty& data);

	bool unsafe_erase(const_iterator pos)noexcept;

};


```
# 📝NOTE THAT: 
THIS IS THE INTERFACE OF THE SINGLE_LINKED_LIST ,WITH THIS INTERFACE YOU CAN MANIPULATE THE LIST. IF YOU WANT MORE DETAILS ABOUT THE IMPLEMENTATION JUST SEE THE List.h and Macros.h for how things are done
also this data structure accepts only elements that are nothrow destructible.
# ⚙️Member functions
1) default constructor this function just creates a list in the default state

2) constructor with initializer list, if the function fails then the list is left in the default state (strong exception guarantee) else we just copy the elements of the initializer list (deep copy)

3) copy constructor is exactly the same as the previous constructor this time the other is a single_linked_list argument, if the function fails then the list is left in the default state (strong exception guarantee)

4) move constructor it just steals the contents of the other list and leaves it in the default state, if this==&other then the list is left in the default state

5) the destructor just deallocates all the list that was allocated (if it was)and returns the list back to the default state if the list is empty this func doesn't do anything

6) push_back,this function just creates a list node and pushes it by copy or move at the end of the list ,if something goes wrong this function doesn't do anything (strong exception guarantee)

7) push_front, this function just creates a list node and pushes it by copy or move at the start of the list,if something goes wrong this function doesn't do anything (strong exception guarantee)

8) pop_front,this function just deletes the first node of the list and updates the list ,if there exists at least one node to delete,WARNING: calling this function while the list is empty will throw an  pop_from_an_empty_list  exception

9) pop_back,this function just deletes the last node of the list and updates the list ,if there exists at least one node to delete,WARNING: calling this function while the list is empty will throw an  pop_from_an_empty_list  exception

10) reverse,this function just reverses the list in place ,if the list is like 1 2 3 the result will be 3 2 1 the reverse process goes like this: 123->213->321

11) insert_after,this function takes an argument pos and a copy of value to insert it after the pos  ,if the pos points to nothing then nothing happens ,if the position is invalid or doesn't belong in the list that called the method an exception will be thrown not_a_valid_position exception

12) add_unique_after has exactly the same behavior as the insert_after function ,the only thing that is different is that if the element is already at the list and we can see this with the help of a comparator passed to this function ,then nothing happens to the list (see implementation for more details of how this works)

13) unique this function simply removes the duplicates in the list if they exist using again a comparator passed to the function ,WARNING: this function considers that the list is sorted and removes the duplicates this way, otherwise we would need another way to tell if there were duplicates in the list in order to remove them (see implementation for more details of how this works) and also if the comp arg throws then the list might delete some elements or not 

14) show,this function just prints all the list elements,use this func only if the values that the container holds can be printed

15) remove,this function simply removes the values of the list that compare equal to the value passed as argument,if something goes wrong  this function might again delete some of the elements in the list that compare equal to the value passed or none of them (see implementation for more details of how this works)

16) remove_if, this function works pretty similar with the remove function but this time we remove elements based on a condition passed by the user (see implementation for more details of how this works)

17) swap,this function simply swaps the contents of two linked lists

18) emplace_back works the same as the push_back function but this time we craft the element in place with the arguments passed and we create the list node

19) emplace_front works the same as the push_front function but this time we craft the element in place with the arguments passed and we create the list node

20) copy operator the copy operator just copies the contents of the other to us ,we make a deep copy ,if something goes wrong the list might change in some way ,or may return to the default state (see implementation for more details of how this works) ,in the while if a copy goes wrong the list is left with some values or none changed if something goes wrong in the if with the push_back we delete what we managed to allocate and return to default state because copy all or copy none

21) move operator ,deallocs our contents and steals the other's contents, WARNING: moving into ourselves will put the list in the default state so will lose our resources

22) copy operator with initializer list as argument works exactly the same way as the original copy operator

23) is_ascending checks if the list is in ascending order using a comparator passed as argument ,if something goes wrong this function doesn't do anything (strong exception guarantee) (see implementation for more details of how this works)

24) is_descending same case but this time if the list is in descending order (strong exception guarantee) (see implementation for more details of how this works)

25) is_sorted only tells if the list is sorted or not ,either in  ascending order or descending order using a comparator passed as argument  (strong exception guarantee) (see implementation for more details of how this works)

26) merge ,this function merges two lists if they are both in ascending order and the other argument is not empty ,also we can't merge into ourselves ,if something goes wrong the behavior is complicated (see implementation for more details of how this works) and read it very carefully ,WARNING:the comparator used to merge the list in order to compare elements must not throw otherwise the behavior is undefined

27) erase_after ,this function takes an iterator pos and deletes the element after this position you gave,if the position is invalid or doesn't belong in the list that called the method an exception will be thrown not_a_valid_position exception

28) unsafe_insert,this function does the same thing as the insert_after function but the only difference is that it doesn' check (for performance reasons) if the iterator passed is invalid or doesn't point to the list that called the method,use this func if you know exactly that the iterator you passed is valid and it shows in the list that called the method be very careful ,otherwise the behavior is undefined

29) unsafe_erase is the same case as erase_after and has the same concept idea as unsafe_insert,use this func with care because it doesn't make checks (this is for performance purposes)

30) empty ,tells if the list is empty

31) size,tells the number of elements that the list currently holds

32) front ,gives the first element of the list

33) back,gives the last element of the list

34) begin,end is for the iterator API (see implementation for more details of how this works) but begin is the start of the list,and end is the end of the list

# 📝NOTE THAT: 
TO SEE HOW THE ITERATOR API WORKS AND THE LIST NODE API, GO TO SEE THE IMPLEMENTATION FOR MORE DETAILS

# 📬IF YOU HAVE ANY ISSEUES ON THIS PLZ FEEL FREE TO SUBMIT THEM 📬
# 👥CONTRIBUTORS:
🎨~Paltoudara
