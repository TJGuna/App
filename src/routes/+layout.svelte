<script>
	import '../app.css';
	import menu from '../assets/svg/menu-burger.svg';
	import left from '../assets/svg/arrow-small-left.svg';
	import right from '../assets/svg/arrow-small-right.svg';

	import logo from '../assets/svg/logo.gif';

	let sidebar = false;
	let mobileView = false;
	let showProfileDropdown = false;
  
</script>

<div>
	{#if mobileView}
	<div class="relative z-40 md:hidden" role="dialog" aria-modal="true">
		<!--
		  Off-canvas menu backdrop, show/hide based on off-canvas menu state.
	
		  Entering: "transition-opacity ease-linear duration-300"
			From: "opacity-0"
			To: "opacity-100"
		  Leaving: "transition-opacity ease-linear duration-300"
			From: "opacity-100"
			To: "opacity-0"
		-->
		<div on:click={()=> mobileView = false} class="fixed inset-0 bg-gray-600 bg-opacity-75"></div>
	
		<div class="fixed h-full z-40 flex">
		  <!--
			Off-canvas menu, show/hide based on off-canvas menu state.
	
			Entering: "transition ease-in-out duration-300 transform"
			  From: "-translate-x-full"
			  To: "translate-x-0"
			Leaving: "transition ease-in-out duration-300 transform"
			  From: "translate-x-0"
			  To: "-translate-x-full"
		  -->
		  <div class="relative flex w-full   flex-col bg-white pt-5 pb-4">
			<!--
			  Close button, show/hide based on off-canvas menu state.
	
			  Entering: "ease-in-out duration-300"
				From: "opacity-0"
				To: "opacity-100"
			  Leaving: "ease-in-out duration-300"
				From: "opacity-100"
				To: "opacity-0"
			-->
			
	
			<div class="mt-5 h-full overflow-y-auto">
			  <nav class="px-2">
				<div class="space-y-1">
				  <!-- Current: "bg-gray-100 text-gray-900", Default: "text-gray-600 hover:bg-gray-50 hover:text-gray-900" -->
				  <a href="#" class="bg-gray-100 text-gray-900 group flex items-center rounded-md px-2 py-2 text-base font-medium leading-5" aria-current="page">
					<!-- Current: "text-gray-500", Default: "text-gray-400 group-hover:text-gray-500" -->
					<svg class="text-gray-500 mr-3 h-6 w-6 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
					  <path stroke-linecap="round" stroke-linejoin="round" d="M2.25 12l8.954-8.955c.44-.439 1.152-.439 1.591 0L21.75 12M4.5 9.75v10.125c0 .621.504 1.125 1.125 1.125H9.75v-4.875c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125V21h4.125c.621 0 1.125-.504 1.125-1.125V9.75M8.25 21h8.25" />
					</svg>
					Home
				  </a>
	
				  <a href="#" class="text-gray-600 hover:bg-gray-50 hover:text-gray-900 group flex items-center rounded-md px-2 py-2 text-base font-medium leading-5">
					<svg class="text-gray-400 group-hover:text-gray-500 mr-3 h-6 w-6 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
					  <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 5.25h16.5m-16.5 4.5h16.5m-16.5 4.5h16.5m-16.5 4.5h16.5" />
					</svg>
					My tasks
				  </a>
	
				  <a href="#" class="text-gray-600 hover:bg-gray-50 hover:text-gray-900 group flex items-center rounded-md px-2 py-2 text-base font-medium leading-5">
					<svg class="text-gray-400 group-hover:text-gray-500 mr-3 h-6 w-6 flex-shrink-0" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" aria-hidden="true">
					  <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v6h4.5m4.5 0a9 9 0 11-18 0 9 9 0 0118 0z" />
					</svg>
					Recent
				  </a>
				</div>
				<div class="mt-8">
				  <h3 class="px-3 text-sm font-medium text-gray-500" id="mobile-teams-headline">Teams</h3>
				  <div class="mt-1 space-y-1" role="group" aria-labelledby="mobile-teams-headline">
					<a href="#" class="group flex items-center rounded-md px-3 py-2 text-base font-medium leading-5 text-gray-600 hover:bg-gray-50 hover:text-gray-900">
					  <span class="mr-4 h-2.5 w-2.5 bg-indigo-500 rounded-full" aria-hidden="true"></span>
					  <span class="truncate">Engineering</span>
					</a>
	
					<a href="#" class="group flex items-center rounded-md px-3 py-2 text-base font-medium leading-5 text-gray-600 hover:bg-gray-50 hover:text-gray-900">
					  <span class="mr-4 h-2.5 w-2.5 bg-green-500 rounded-full" aria-hidden="true"></span>
					  <span class="truncate">Human Resources</span>
					</a>
	
					<a href="#" class="group flex items-center rounded-md px-3 py-2 text-base font-medium leading-5 text-gray-600 hover:bg-gray-50 hover:text-gray-900">
					  <span class="mr-4 h-2.5 w-2.5 bg-yellow-500 rounded-full" aria-hidden="true"></span>
					  <span class="truncate">Customer Success</span>
					</a>
				  </div>
				</div>
			  </nav>
			</div>
		  </div>
	
		 
		</div>
	  </div>
	
	{/if} 
	 <!-- Static sidebar for desktop -->
	<div class="hidden md:fixed md:inset-y-0 md:flex {sidebar? 'w-14':'w-40'} md:flex-col mt-16   transition-[width]">
		<!-- Sidebar component, swap this element with another sidebar if you like -->
		<div class="flex flex-grow flex-col overflow-y-auto border-r border-gray-200 bg-white pt-5">
			<div class=" flex flex-grow flex-col">
				<nav class="flex-1 space-y-1 px-2 pb-4">
					<!-- Current: "bg-gray-100 text-gray-900", Default: "text-gray-600 hover:bg-gray-50 hover:text-gray-900" -->
					<a
						href="#"
						class="bg-gray-100 text-gray-900 group flex items-center rounded-md px-2 py-2 text-sm font-medium"
					>
						<!-- Current: "text-gray-500", Default: "text-gray-400 group-hover:text-gray-500" -->
						<svg
							class="text-gray-500 mr-3 h-6 w-6 flex-shrink-0"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							aria-hidden="true"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M2.25 12l8.954-8.955c.44-.439 1.152-.439 1.591 0L21.75 12M4.5 9.75v10.125c0 .621.504 1.125 1.125 1.125H9.75v-4.875c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125V21h4.125c.621 0 1.125-.504 1.125-1.125V9.75M8.25 21h8.25"
							/>
						</svg>
						<span class="{sidebar ? 'hidden':'block'}">Dashboard</span>
						
					</a>

					<a
						href="/orders"
						class="text-gray-600 hover:bg-gray-50 hover:text-gray-900 group flex items-center rounded-md px-2 py-2 text-sm font-medium"
					>
						<svg
							class="text-gray-400 group-hover:text-gray-500 mr-3 h-6 w-6 flex-shrink-0"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							aria-hidden="true"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M15 19.128a9.38 9.38 0 002.625.372 9.337 9.337 0 004.121-.952 4.125 4.125 0 00-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128v.106A12.318 12.318 0 018.624 21c-2.331 0-4.512-.645-6.374-1.766l-.001-.109a6.375 6.375 0 0111.964-3.07M12 6.375a3.375 3.375 0 11-6.75 0 3.375 3.375 0 016.75 0zm8.25 2.25a2.625 2.625 0 11-5.25 0 2.625 2.625 0 015.25 0z"
							/>
						</svg>
						<span class="{sidebar ? 'hidden':'block'}">Orders</span>

						
					</a>

					<a
						href="#"
						class="text-gray-600 hover:bg-gray-50 hover:text-gray-900 group flex items-center rounded-md px-2 py-2 text-sm font-medium"
					>
						<svg
							class="text-gray-400 group-hover:text-gray-500 mr-3 h-6 w-6 flex-shrink-0"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							aria-hidden="true"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M2.25 12.75V12A2.25 2.25 0 014.5 9.75h15A2.25 2.25 0 0121.75 12v.75m-8.69-6.44l-2.12-2.12a1.5 1.5 0 00-1.061-.44H4.5A2.25 2.25 0 002.25 6v12a2.25 2.25 0 002.25 2.25h15A2.25 2.25 0 0021.75 18V9a2.25 2.25 0 00-2.25-2.25h-5.379a1.5 1.5 0 01-1.06-.44z"
							/>
						</svg>
						<span class="{sidebar ? 'hidden':'block'}">Projects</span>

						
					</a>

					<a
						href="#"
						class="text-gray-600 hover:bg-gray-50 hover:text-gray-900 group flex items-center rounded-md px-2 py-2 text-sm font-medium"
					>
						<svg
							class="text-gray-400 group-hover:text-gray-500 mr-3 h-6 w-6 flex-shrink-0"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							aria-hidden="true"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 012.25-2.25h13.5A2.25 2.25 0 0121 7.5v11.25m-18 0A2.25 2.25 0 005.25 21h13.5A2.25 2.25 0 0021 18.75m-18 0v-7.5A2.25 2.25 0 015.25 9h13.5A2.25 2.25 0 0121 11.25v7.5"
							/>
						</svg>
						<span class="{sidebar ? 'hidden':'block'}">Calendar</span>

						
					</a>

					<a
						href="#"
						class="text-gray-600 hover:bg-gray-50 hover:text-gray-900 group flex items-center rounded-md px-2 py-2 text-sm font-medium"
					>
						<svg
							class="text-gray-400 group-hover:text-gray-500 mr-3 h-6 w-6 flex-shrink-0"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							aria-hidden="true"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M2.25 13.5h3.86a2.25 2.25 0 012.012 1.244l.256.512a2.25 2.25 0 002.013 1.244h3.218a2.25 2.25 0 002.013-1.244l.256-.512a2.25 2.25 0 012.013-1.244h3.859m-19.5.338V18a2.25 2.25 0 002.25 2.25h15A2.25 2.25 0 0021.75 18v-4.162c0-.224-.034-.447-.1-.661L19.24 5.338a2.25 2.25 0 00-2.15-1.588H6.911a2.25 2.25 0 00-2.15 1.588L2.35 13.177a2.25 2.25 0 00-.1.661z"
							/>
						</svg>
						<span class="{sidebar ? 'hidden':'block'}">Documents</span>

						
					</a>

					<a
						href="#"
						class="text-gray-600 hover:bg-gray-50 hover:text-gray-900 group flex items-center rounded-md px-2 py-2 text-sm font-medium"
					>
						<svg
							class="text-gray-400 group-hover:text-gray-500 mr-3 h-6 w-6 flex-shrink-0"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							aria-hidden="true"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M3 13.125C3 12.504 3.504 12 4.125 12h2.25c.621 0 1.125.504 1.125 1.125v6.75C7.5 20.496 6.996 21 6.375 21h-2.25A1.125 1.125 0 013 19.875v-6.75zM9.75 8.625c0-.621.504-1.125 1.125-1.125h2.25c.621 0 1.125.504 1.125 1.125v11.25c0 .621-.504 1.125-1.125 1.125h-2.25a1.125 1.125 0 01-1.125-1.125V8.625zM16.5 4.125c0-.621.504-1.125 1.125-1.125h2.25C20.496 3 21 3.504 21 4.125v15.75c0 .621-.504 1.125-1.125 1.125h-2.25a1.125 1.125 0 01-1.125-1.125V4.125z"
							/>
						</svg>
						<span class="{sidebar ? 'hidden':'block'}">Reports</span>

						
					</a>
				</nav>
			</div>
			<span on:click={()=> sidebar =! sidebar} class="absolute  md:block bottom-8 -right-4 rounded-full bg-white p-1 border"> 
				<img src={right} alt="" class="{!sidebar ? 'hidden':'block'} w-6"/>
				<img src={left} alt="" class="{sidebar ? 'hidden':'block'} w-6"/>
			</span>
		</div>
	</div>
	<div class="flex flex-1 flex-col ">
		<div id='toolbar' class=" px-4 fixed  z-10  h-16 w-full mx-auto bg-white border-b  flex items-center justify-between">

			<div on:click={() => mobileView =! mobileView} class="flex items-center md:hidden">
				<img src={menu} alt="menu" class="w-6"/>
			</div>
			<div class="flex  items-center  px-4 text-gray-500 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-500 ">
				<img src={logo} alt="menu" class="w-12"/>
				<p class="hidden sm:block">Company Name</p>
			</div>
			<div class="flex  justify-between px-4">
				<div class="ml-4 flex items-center md:ml-6">
					<button
						type="button"
						class="rounded-full bg-white p-1 text-gray-400 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
					>
						<span class="sr-only">View notifications</span>
						<svg
							class="h-6 w-6"
							fill="none"
							viewBox="0 0 24 24"
							stroke-width="1.5"
							stroke="currentColor"
							aria-hidden="true"
						>
							<path
								stroke-linecap="round"
								stroke-linejoin="round"
								d="M14.857 17.082a23.848 23.848 0 005.454-1.31A8.967 8.967 0 0118 9.75v-.7V9A6 6 0 006 9v.75a8.967 8.967 0 01-2.312 6.022c1.733.64 3.56 1.085 5.455 1.31m5.714 0a24.255 24.255 0 01-5.714 0m5.714 0a3 3 0 11-5.714 0"
							/>
						</svg>
					</button>

					<div class="relative ml-3">
						<div>
							<button
								type="button"
								on:click={() => (showProfileDropdown = !showProfileDropdown)}
								class="flex max-w-xs items-center rounded-full bg-white text-sm focus:outline-none focus:ring-2 focus:ring-indigo-500 focus:ring-offset-2"
								id="user-menu-button"
								aria-expanded="false"
								aria-haspopup="true"
							>
								<span class="sr-only">Open user menu</span>
								<img
									class="h-8 w-8 rounded-full"
									src="https://images.unsplash.com/photo-1472099645785-5658abf4ff4e?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80"
									alt=""
								/>
							</button>
						</div>

					
						{#if showProfileDropdown}
							<div
								class="h-full fixed z-20 left-0 top-0 w-full "
								on:click={() => (showProfileDropdown = false)}
							/>
							<div
								class="absolute z-30 right-0 z-10 mt-2 w-48 origin-top-right rounded-md bg-white py-1 shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
								role="menu"
								aria-orientation="vertical"
								aria-labelledby="user-menu-button"
								tabindex="-1"
							>
								<a
									href="#"
									class="block px-4 py-2 text-sm text-gray-700"
									role="menuitem"
									tabindex="-1"
									id="user-menu-item-0">Your Profile</a
								>

								<a
									href="#"
									class="block px-4 py-2 text-sm text-gray-700"
									role="menuitem"
									tabindex="-1"
									id="user-menu-item-1">Settings</a
								>

								<a
									href="#"
									class="block px-4 py-2 text-sm text-gray-700"
									role="menuitem"
									tabindex="-1"
									id="user-menu-item-2">Sign out</a
								>
							</div>
						{/if}
					</div>
				</div>
			</div>
		</div>

		<main>
			<div class="mx-auto transition-[width]  {sidebar ? 'md:pl-14' : 'md:pl-40'} " >
				<div class="p-4 bg-gray-100 mt-16 min-h-full">
					<slot /> 
				</div>
			</div>
		</main>
	</div>
</div>
