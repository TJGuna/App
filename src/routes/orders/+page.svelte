<script lang="ts">
	import Table from "../components/table/table.svelte";
    import PageHeader from "../components/page-header.svelte";
    import PageBody from "../components/page-body.svelte";
    import table from "../../mock/orders.json";

    const columns = [
  { key: 'id', title: 'ID', sortable: true },
  { key: 'name', title: 'Name', sortable: true },
  { key: 'age', title: 'Age', sortable: true },
  { key: 'email', title: 'Email', sortable: false },
  { key: 'phone_number', title: 'Phone Number', sortable: false },
  { key: 'full_address', title: 'Address', sortable: false },
  { key: 'city', title: 'City', sortable: true },
  { key: 'province', title: 'Province/State', sortable: true },
  { key: 'postalcode', title: 'Postal Code', sortable: true },
  { key: 'country', title: 'Country', sortable: true },
  { key: 'active', title: 'Active', sortable: false }
];
let searchableColumns = ['id','name', 'age', 'email', 'phone_number', 'full_address', 'city', 'province', 'postalcode', 'country', 'active'];
let availableColumns = ['id','name', 'age', 'email', 'full_address', 'city', 'active'];
 let actions = true;
 let actionList = ['Edit', 'Delete'];
 let bulckActions = ['Activate', 'Deactivate', 'Delete', 'Export to CSV', 'Export to PDF'];

 const rows = table;
</script>
<PageHeader Title="Orders" >
        <button class="px-2 py-1 border rounded text-white bg-[#62CDFF]">Add New Order</button>
</PageHeader>
<PageBody>
    <Table {columns} {rows} {availableColumns} {searchableColumns} {actions} {actionList} {bulckActions} />
</PageBody>