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
THIS IS THE INTERFACE OF THE SINGLE_LINKED_LIST WITH THIS INTERFACE YOU CAN MANIPULATE THE LIST. IF YOU WANT MORE DETAILS ABOUT THE IMPLEMENTATION JUST SEE THE header.h and Macros.h for how things are done
also this data structure  accepts only elements that are nothrow destructible.
# ⚙️Member functions
1) default constructor: this function just creates a list in the default state

2) constructor with initializer list, if the function fails then the list is left in the default state (strong exception guarantee)

3) copy constructor is exactly the same as the previous constructor this time other is a single_linked_list argument (strong exception guarantee)

4) move constructor it just steals the contents of the other list and leaves it in the default state, if this==&other then the list is left in the default state

5) the destructor just deallocates all the list that was allocated (if it was)and returns the list back to the default state if the list is empty this func doesn't do anything

6) push_back,this function just creates a list node and pushes it by copy or move at the end of the list ,if something goes wrong this function doesn't do anything (strong exception guarantee)

7) push_front, this function just creates a list node and pushes it by copy or move at the start of the list,if something goes wrong this function doesn't do anything (strong exception guarantee)

8) pop_front,this function just deletes the first node of the list and updates the list ,if there exists one node to delete,WARNING: calling this function while the list is empty will throw an  pop_from_an_empty_list  exception

9) pop_back,this function just deletes the last node of the list and updates the list ,if there exists one node to delete,WARNING: calling this function while the list is empty will throw an  pop_from_an_empty_list  exception

10) reverse,this function just reverses the list in place ,if the list is like 1 2 3 the result will be 3 2 1

11) insert_after,this function takes an argument pos and a copy of value to insert it ,if the pos points to nothing then nothing happens ,if the position is invalid or doesn't belong in the list that called the method an exception will be thrown not_a_valid_position exception

12) add_unique_after has exactly the same behavior as the insert_after function ,the only thing that is different is that if the element is already at the list and we can see this with the help of a comparator passed to this function ,then nothing happens to the list (see implementation for more details of how this works)

13) unique this function simply removes the duplicates in the list if they exist using again a comparator passed to the function ,WARNING: this function considers that the list is sorted and removes the duplicates this way, otherwise we would need another way to tell if there were duplicates in the list in order to remove them (see implementation for more details of how this works)
