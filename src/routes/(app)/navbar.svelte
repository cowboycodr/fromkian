<script>
	import { page } from '$app/stores';

	import { Navbar } from '$components/navbar';
	import { Button } from '$ui/button';
	import * as Sheet from '$ui/sheet';

	let { session } = $page.data;
	$: ({ session } = $page.data);
</script>

<Navbar>
	<nav class="container w-full p-0 py-2">
		<div class="flex justify-between">
			<div class="flex items-center">
				<Button
						href="/"
						class="text-lg font-normal"
						variant="ghost"
						size="sm"
					>
						<h3 class="text-lg">Kian McKenna</h3>
					</Button>
			</div>
			<div class="flex items-center space-x-1">
				<div>
					<Button
						href="https://github.com/cowboycodr"
						class="text-lg font-normal"
						variant="ghost"
						size="sm"
						target="_blank"
					>
						github
					</Button>
				</div>
				<div>
					<Sheet.Root>
						<Sheet.Trigger asChild let:builder>
							<Button
								builders={[builder]}
								class="text-lg font-normal"
								variant="ghost"
								size="sm"
								aria-label="Menu"
							>
								menu
							</Button>
						</Sheet.Trigger>
						<Sheet.Content class="flex h-full flex-col">
							<Sheet.Header>
								<Sheet.Title>menu</Sheet.Title>
							</Sheet.Header>
							<div class="flex-grow">
								<!-- Menu content goes here -->
							</div>
							<Sheet.Footer>
								{#if session}
									<form class="w-full" method="POST" action="/auth?/signout">
										<Button class="w-full" variant="secondary" type="submit">Sign out</Button>
									</form>
								{:else}
									<div class="flex w-full flex-col space-y-1">
										<Button href="/auth/login" variant="secondary" size="sm">Log in</Button>
										<Button href="/auth/signup" size="sm">Sign up</Button>
									</div>
								{/if}
							</Sheet.Footer>
						</Sheet.Content>
					</Sheet.Root>
				</div>
			</div>
		</div>
	</nav>
</Navbar>
