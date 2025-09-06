# 🔗 Welcome to the _SINGLE_LINKED_LIST_ API 🌐:
# 🧩 Interface:
```markdown
```cpp
template<typename _Ty>
class vector final {
public:
	using iterator = vector_iterator<true>;
	using const_iterator = vector_iterator<false>;

	vector()noexcept;

	vector(const std::size_t capacity);

	vector(const vector<_Ty>& other);

	vector(const std::initializer_list<_Ty>& other);

	vector(vector<_Ty>&& other)noexcept;

	std::size_t capacity()const noexcept;

	bool empty()const noexcept;

	std::size_t size()const noexcept;

	void push_back(const _Ty& data);

	void push_back(_Ty&& data);

	template<class ..._Valty>
	void emplace_back(_Valty&&..._Val);

	void pop_back()noexcept;

	void show() const;

	const _Ty& operator [](const std::size_t index) const&;

	_Ty& operator [](const std::size_t index)&;

	_Ty&& operator [](const std::size_t index)&&;

	const _Ty&& operator [](const std::size_t index)const&&;

	const _Ty& at(const std::size_t index) const&;

	_Ty&at(const std::size_t index)&;
	
	_Ty&& at(const std::size_t index)&&;

	const _Ty&& at(const std::size_t index)const&&;

	~vector()noexcept;

	void clear()noexcept;

	const _Ty& front() const&;

	_Ty& front()&;

	_Ty&& front()&&;

	const _Ty&& front()const&&;

	const _Ty& back() const&;

	_Ty& back()&;

	_Ty&& back()&&;

	const _Ty&& back()const&&;

	void swap(vector<_Ty>& other)noexcept;

	void reserve(const std::size_t new_capacity);

	void shrink_to_fit();

	void resize(const std::size_t new_size);

	void resize(const std::size_t new_size, const _Ty& value);

	vector<_Ty>& operator =(const vector<_Ty>& other)&;

	void assign(const std::size_t count, const _Ty& value);

	vector<_Ty>& operator =(vector<_Ty>&& other) & noexcept;

	vector<_Ty>& operator =(const std::initializer_list<_Ty>& other)&;

	_Ty** data()noexcept;

	void insert(const std::size_t index, const _Ty& value);

	void insert(const std::size_t index, _Ty&& value);

	template<class..._Valty>
	void emplace(const std::size_t index, _Valty&&..._Val);

	void erase(const std::size_t index)noexcept;

	iterator begin()noexcept;

	iterator end()noexcept;

	const_iterator cbegin()noexcept;

	const_iterator cend()noexcept;

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
