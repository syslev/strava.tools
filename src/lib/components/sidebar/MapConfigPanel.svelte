<script lang="ts">
	import * as Card from '$lib/components/ui/card';
	import * as Select from '$lib/components/ui/select';
	import * as Dropdown from '$lib/components/ui/dropdown-menu';
	import Button from '$lib/components/ui/button/button.svelte';
	import { Separator } from '$lib/components/ui/separator';
	import { Label } from '$lib/components/ui/label';
	import { Switch } from '$lib/components/ui/switch';
	import BasemapSelect from '$lib/components/sidebar/map-config-components/BasemapSelect.svelte';
	import ActivityTypeSelect from '$lib/components/settings/ActivityTypeSelect.svelte';
	import type { StravaActivity } from '$lib/activities';

	export let activityTypeFilter: string;
	export let showPrivate: boolean = true;
</script>

<div class="w-full px-6 flex flex-col gap-3">
	<ActivityTypeSelect bind:value={activityTypeFilter} />
	<div class="pl-2 pt-s1">
		<Label for="private-activities" class="bottom-1 pr-1 relative select-none text-sm font-medium"
			>Show Private Activities</Label
		>
		<Switch
			id="private-activities"
			bind:checked={showPrivate}
			class="data-[state=checked]:bg-secondary"
		/>
	</div>
	<Separator class="w-auto" />
	<BasemapSelect />
</div>
