# shashogo woreda integrated digital system function Search() {
  const [search, setSearch] = React.useState('');
  const { data, isLoading } = useSWR(`/search?q=${search}`, fetcher, {
    keepPreviousData: true
  });
  return (
    <div>
      <input
        type="text"
        value={search}
        onChange={(e) => setSearch(e.target.value)}
        placeholder="Search..."
      />
      <div className={isLoading ? "loading" : ""}>
        {data?.products.map(item => <Product key={item.id} name={item.name} />)
      </div>
    </div>
  );
}