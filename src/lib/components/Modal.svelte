<script lang="ts">
	let {
		showModal = $bindable(),
		children
	}: { showModal: boolean; children?: import('svelte').Snippet } = $props();

	let dialog = $state<HTMLDialogElement>();

	$effect(() => {
		if (showModal) dialog?.showModal();
		else dialog?.close();
	});
</script>

<!-- svelte-ignore a11y_click_events_have_key_events a11y_no_noninteractive_element_interactions -->
<dialog
	bind:this={dialog}
	onclose={() => (showModal = false)}
	onclick={(e) => {
		if (e.target === dialog) dialog?.close();
	}}
>
	<button class="close-btn" onclick={() => dialog?.close()} aria-label="Close">✕</button>
	<div class="modal-body">
		{@render children?.()}
	</div>
</dialog>

<style>
	dialog {
		background: #111111;
		color: white;
		border: none;
		border-radius: 10px;
		padding: 0;
		width: min(92vw, 360px);
		overflow: hidden;
		position: fixed;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
	}

	dialog::backdrop {
		background: rgba(0, 0, 0, 0.7);
		backdrop-filter: blur(6px);
	}

	dialog[open] {
		animation: modal-in 0.28s cubic-bezier(0.34, 1.56, 0.64, 1) forwards;
	}

	@keyframes modal-in {
		from {
			opacity: 0;
			transform: translate(-50%, -50%) scale(0.88);
		}
		to {
			opacity: 1;
			transform: translate(-50%, -50%) scale(1);
		}
	}

	dialog[open]::backdrop {
		animation: backdrop-in 0.2s ease forwards;
	}

	@keyframes backdrop-in {
		from {
			opacity: 0;
		}
		to {
			opacity: 1;
		}
	}

	.close-btn {
		position: absolute;
		top: 0.65rem;
		right: 0.65rem;
		background: rgba(255, 255, 255, 0.1);
		border: none;
		color: white;
		width: 2rem;
		height: 2rem;
		border-radius: 50%;
		cursor: pointer;
		font-size: 0.65rem;
		display: flex;
		align-items: center;
		justify-content: center;
		transition: background 0.2s;
		z-index: 1;
	}

	.close-btn:hover {
		background: rgba(255, 255, 255, 0.2);
	}

	.modal-body {
		padding: 0;
	}
</style>
