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
AN entire single_linked_list with all the basic features:
<br>
1. an  inside class of the simple list node with constructors<br>
~the default<br>
~with const element<br>
~with move element<br>
~and a private constructor used to craft the object in place (see implementation)
2. an inside class of simple iterator (pretty much a wrapper around a pointer that points to a node or to nothing nullptr)
   with the iterator you have access to change the element or to see it and advance
   operations supported: operator ++ ,!=,==,*,+=,->,+,copy operator and move operator and a simple destructor
   
3. another inside class of a simple const iterator (pretty much a wrapper around a pointer that points to a node or to nothing nullptr),
    with this kind of iterator you can just get the element for reading not writing it also supports same operations with the other iterator <br>
4. the private members head,tail,count in order to maintain and manipulate the list 
5. push_back function which puts the element at  the end of the list
6. push_front function  which put the element at the start of the list 
7. pop_front which delete the first element of the list 
8. pop_back which delete the last element of the list
9. clear this function is used to deallocate the list 
10. reverse func this just reverses the list
11. insert element justs inserts the element but considers that the list is sorted because sorting a list is already a very expensive operation
12. delete duplicates ,it just deletes the duplicates again we consider that the list is sorted if it is not we might want to use a hashset in order to keep track of the elements
13. erase_node_if erases nodes of the list if a certain condition is met with the help of the passed function the argument _Pred
14. emplace_back same as push_back it just constructs the object in place the only difference
15. emplace_front same as push_front it just constructs the object in place the only difference
16. start funcs finish funcs and cstart funcs and cend funcs they just return an iterator or const iterator to the start of the list the head or the end we consider the end to be nullptr
17. merge lists just combines two lists and leaves the other empty
18. is_ascending_ checks if the elements are in ascending order using a compare func
19. is_descending_ checks if the elements are in descending order using a compare func
20. is sorted checks if the elements are either sorted in  ascending or descending order

# 👥CONTRIBUTORS:

~Paltoudara
