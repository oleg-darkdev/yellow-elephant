<script>
	import Timer from '../components/tournaments/Timer.svelte';
	import Organisator from '../components/tournaments/Organisator.svelte';
	import Awards from '../components/tournaments/Awards.svelte';
	import BecomeOrganisator from '../components/tournaments/BecomeOrganisator.svelte';
	import { onMount } from 'svelte';
	import Footer from '../components/Footer.svelte';
	import ListTournaments from '../components/tournaments/ListTournaments.svelte';
	import tournamentData from '../data/chessTurnamentsList';
	import DescriptionChess from '../components/DescriptionChess.svelte';
	import sponsors from '../data/sponsors';
	import organisators from '../data/organisators';
	import socialMedia from '../data/socialMedia';

	let firstColumnData = [
		'Turniej szachowy "Żółty Słoń"',
		[
			{
				title: 'O turnieju',
				link: 'https://yellow-elephant.vercel.app/checkers#about'
			},
			{
				title: 'Regulamin',
				link: 'https://yellow-elephant.vercel.app/checkers#terms'
			},
			{
				title: 'Nagrody',
				link: 'https://yellow-elephant.vercel.app/checkers#awards'
			},
			{
				title: 'Sędzia',
				link: 'https://yellow-elephant.vercel.app/checkers#referee'
			},
			{
				title: 'Historia',
				link: 'https://yellow-elephant.vercel.app/checkers#hronology'
			}
		]
	];

	let secondColumnData = [
		`Partnerzy`,
		[
			{
				title: 'Sopoteka',
				link: 'https://www.mbp.sopot.pl/'
			},
			{
				title: 'ITingo',
				link: ''
			},
			{
				title: '44games',
				link: ''
			},
			{
				title: 'MasterMind',
				link: 'https://www.linkedin.com/groups/8773508/'
			},
			// {
			// 	title: 'Lorem',
			// 	link: ''
			// },
			// {
			// 	title: 'Lorem',
			// 	link: ''
			// }
		]
	];
	let thirdColumnData = [
		'Kontakt',
		[
			{
				title: 'Facebook',
				link: 'https://www.facebook.com/hulio.mondre'
			},
			{
				title: 'LinkedIn',
				link: 'https://www.linkedin.com/in/oleg-darkdev?original_referer=https%3A%2F%2Flinktr.ee%2F'
			},
			{
				title: 'Email',
				link: 'mailto:oleg@darkdev.games'
			}
		]
	];

	onMount(() => {
		startTimer();
	});

	const tournamentDay = '1/',
		tournamentMonth = '04/';

	// Timer
	async function startTimer() {
		const second = 1000,
			minute = second * 60,
			hour = minute * 60,
			day = hour * 24;

		let today = new Date(),
			dd = String(today.getDate()).padStart(2, '0'),
			mm = String(today.getMonth() + 1).padStart(2, '0'),
			yyyy = today.getFullYear(),
			nextYear = yyyy + 1,
			dayMonth = tournamentMonth.concat(tournamentDay),
			tournament = dayMonth + yyyy;

		today = mm + '/' + dd + '/' + yyyy;
		if (today > tournament) {
			tournament = dayMonth + nextYear;
		}
		//end

		const countDown = new Date(tournament).getTime(),
			x = setInterval(function () {
				const now = new Date().getTime(),
					distance = countDown - now;

				(document.getElementById('days').innerText = Math.floor(distance / day)),
					(document.getElementById('hours').innerText = Math.floor((distance % day) / hour)),
					(document.getElementById('minutes').innerText = Math.floor((distance % hour) / minute)),
					(document.getElementById('seconds').innerText = Math.floor((distance % minute) / second));

				if (distance < 0) {
					document.getElementById('headline').innerText = 'Turniej odbędzie się dzisiaj!';
					document.getElementById('countdown').style.display = 'none';
					clearInterval(x);
				}
				//seconds
			}, 0);
	}
</script>

<svelte:head>
	<title>Żółty słoń</title>
</svelte:head>

<main class="bg-light">
	<section class="banner w-full pb-12 flex flex-col items-center">
		<div class="lg:mt-10 lg:bg-transparent  md:bg-transparent  bg-white w-full flex justify-center">
			<ul class="flex flex-row  mt-4 md:space-x-8 md:mt-0 md:text-sm md:font-medium ">
				<li>
					<a
						href="#about"
						class="lg:text-3xl text-1xl block py-2 pr-2 pl-2 md:p-0 rounded md:border-0 font-impact text-dark hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-dark  "
					>
						O turnieju
					</a>
				</li>
				<li>
					<a
						href="#terms"
						class="lg:text-3xl text-1xl  block py-2 pr-2 pl-2 md:p-0 rounded md:border-0 font-impact text-dark hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-dark  "
					>
						Regulamin
					</a>
				</li>
				<li>
					<a
						href="#awards"
						class="lg:text-3xl text-1xl  block py-2 pr-2 pl-2 md:p-0 rounded md:border-0 font-impact text-dark hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-dark  "
					>
						Nagrody
					</a>
				</li>
				<li>
					<a
						href="#referee"
						class="lg:text-3xl text-1xl  block py-2 pr-2 pl-2 md:p-0 rounded md:border-0 font-impact text-dark hover:bg-gray-100 md:hover:bg-transparent md:border-0 md:hover:text-dark  "
					>
						Sędzia
					</a>
				</li>
			</ul>
		</div>

		<h1
			class=" lg:pt-10 md:pt-10 pt-2 text-center text-white font-impact xl:text-6xl lg:text-6xl md:text-5xl text-3xl lg:max-w-2xl lg:w-8/12 w-10/12"
		>
			Comiesięczny turniej szachowy "Żółty Słoń"
		</h1>
	</section>

	<a id="about" />
	<section class="w-full h-auto lg:pb-12 md:pb-12 pb-12 flex justify-center">
		<div
			data-aos="fade-up"
			data-aos-delay="100"
			data-aos-duration="1000"
			data-aos-once="false"
			data-aos-mirror="true"
			class="m-1 h-auto rounded-lg max-w-2xl bg-dark lg:p-8 md:p-8 p-2 flex flex-col items-center"
		>
			<DescriptionChess>
				<div slot="text">
					<p class="text-gray-100 text-2xl mb-4 text-center">
						W tym turnieju szachów klasycznych znajdzie się miejsce zarówno dla amatorów jak i tych
						bardziej zaawansowanych graczy. <span class="text-light "
							>Ranking graczy 1400-2000.</span
						>
					</p>
					<p class="text-gray-100 text-2xl mb-4 text-center">
						Uczestnictwo jest bezpłatne. Zgłoszenie rejestrowane drogą mailową <span
							class="inline-flex items-center  text-light ">yellow_elephant.pl@outlook.com</span
						>, oraz poprzez zapisy przed rozpoczęciem turnieju.
					</p>
					<!-- <p class="text-gray-100 text-2xl mb-4">
            Wpisowe wynosi 5 zł i jest płatne podczas rejestracji w formularzu turniejowym przed rozpoczęciem turnieju.
        </p>     -->
					<p class="text-gray-100 text-2xl mb-4 text-center">
						Ogłoszenia o terminach dostępne są w mediach socjalnych.
					</p>
				</div>

				<div slot="timer">
					<Timer />
				</div>
				<div
					slot="hronology"
					id="hronology"
					class="mb-4 max-w-2xl justify-center items-center bg-current text-gray-500 rounded-lg flex w-full flex-col p-2 sm:p-4"
				>
					<h2 class="text-3xl max-w-xl text-center mb-2 font-impact text-light ">
						Harmonogram turnieju szachowego "Żółty Słoń
					</h2>

					<ListTournaments {tournamentData} />
				</div>
			</DescriptionChess>
		</div>
	</section>

	<a name="sponsors" />
	<section class="partners bg-dark w-full pt-12 pb-12 flex flex-col items-center">
		<h2
			class="w-full text-center text-white font-impact lg:text-5xl md:text-4xl text-4xl max-w-3xl "
		>
			Sponsorzy
		</h2>
		<div class="flex flex-row flex-wrap w-full justify-center mb-2">
			{#each sponsors as sponsor}
				<a href={sponsor.link} target="_blank">
					<div
						class="hover:border-light hover:border-4 rounded-lg m-1"
						style="background-image: url({sponsor.logo}); width: 220px; height: 110px;"
					/>
				</a>
			{/each}
		</div>
		<h2
			class="w-full text-center text-white font-impact lg:text-5xl md:text-4xl text-4xl max-w-3xl "
		>
			Organizatorzy
		</h2>
		<div class="flex flex-row flex-wrap w-full justify-center mb-10">
			{#each organisators as organisator}
				<a href={organisator.link} target="_blank">
					<div
						class="hover:border-light hover:border-4 rounded-lg m-1 "
						style="background-image: url({organisator.logo}); width: 220px; height: 110px;"
					/>
				</a>
			{/each}
		</div>

		<div class="bg-light  rounded-lg  shadow-md flex max-w-2xl flex-col p-4 sm:p-8 text-center">
			<BecomeOrganisator>
				<div slot="text">
					<p class="text-gray-100 text-2xl mb-4 text-center">
						W tym turnieju szachów klasycznych znajdzie się miejsce zarówno dla amatorów jak i tych
						bardziej zaawansowanych graczy. <span class="text-light "
							>Ranking graczy 1400-2000.</span
						>
					</p>
					<p class="text-gray-100 text-2xl mb-4 text-center">
						Uczestnictwo jest bezpłatne. Zgłoszenie rejestrowane drogą mailową <span
							class="inline-flex items-center  text-light ">yellow_elephant.pl@outlook.com</span
						>, oraz poprzez zapisy przed rozpoczęciem turnieju.
					</p>
					<!-- <p class="text-gray-100 text-2xl mb-4">
            Wpisowe wynosi 5 zł i jest płatne podczas rejestracji w formularzu turniejowym przed rozpoczęciem turnieju.
        </p>     -->
					<p class="text-gray-100 text-2xl mb-4 text-center">
						Ogłoszenia o terminach dostępne są w mediach socjalnych.
					</p>
				</div>
			</BecomeOrganisator>

			<div class="flex flex-col flex-wrap w-full items-center">
				<p class="text-white text-4xl m-1 max-w-2xl text-center" />
				<div class="flex flex-row " />
			</div>
		</div>
	</section>

	<a id="terms" />
	<section class="w-full pt-12 pb-12 h-auto flex flex-col items-center bg-gray-100">
		<h2
			class="w-full text-center text-dark font-impact lg:text-5xl md:text-4xl text-4xl max-w-3xl "
		>
			Regulamin turnieju "Żółty słoń"
		</h2>
		<div class="flex flex-row flex-wrap w-full  justify-center cards-wrap">
			<div
				data-aos="fade-up"
				data-aos-delay="100"
				data-aos-duration="1000"
				data-aos-once="false"
				data-aos-mirror="true"
				style="background-image: url(/terms/terms_clocks.svg);"
				class="card-term items-end flex"
			>
				<div
					style="height: 200px; width: 360px;"
					class="bg-dark text-light rounded-lg border border-light shadow-md flex max-w-sm flex-col lg:p-4 md:p-4 p-2"
				>
					<span class="text-8xl font-impact tracking-tight text-white text-center"> 10 min. </span>
					<span class="text-4xl font-impact tracking-tight text-white text-center">
						na jednego gracza
					</span>
				</div>
			</div>
			<div
				data-aos="fade-down"
				data-aos-delay="100"
				data-aos-duration="1000"
				data-aos-once="false"
				data-aos-mirror="true"
				style="background-image: url(/terms/terms_ranking.svg); "
				class="max-w-sm card-ranking items-center flex"
			>
				<div
					style="height: 180px; width: 360px;"
					class="bg-dark text-light rounded-lg border border-light shadow-md flex max-w-sm flex-col lg:p-4 md:p-4 p-2 "
				>
					<span class="text-4xl font-impact tracking-tight text-white text-center">
						Rankinging
					</span>
					<span class="text-7xl font-impact tracking-tight text-white text-center">
						1400-2000
					</span>
				</div>
			</div>

			<div
				data-aos="fade-up"
				data-aos-delay="100"
				data-aos-duration="1000"
				data-aos-once="false"
				data-aos-mirror="true"
				style="background-image: url(/terms/terms_system.svg); "
				class="card-term items-end flex"
			>
				<div
					style="height: 200px; width: 360px; justify-content: center; "
					class="bg-dark text-light rounded-lg border border-light shadow-md flex  max-w-sm flex-col lg:p-4 md:p-4 p-2"
				>
					<span class="text-6xl font-impact tracking-tight text-white text-center">
						Szwajcarski
					</span>
					<span class="text-4xl font-impact tracking-tight text-white text-center">
						system rozgrywek
					</span>
				</div>
			</div>
		</div>
	</section>

	<a id="awards" />
	<section class="w-full pt-12 pb-12 h-auto flex flex-col items-center bg-dark">
		<Awards />
	</section>

	<a id="referee" />
	<section class="w-full h-auto flex justify-center bg-gray-100">
		<Organisator />
	</section>

	<!-- <section  class="w-full flex flex-col items-center pt-12 pb-12 h-auto">
		<div id="hronology"
			class="mb-4 max-w-2xl justify-center items-center bg-current text-gray-500 rounded-lg flex w-full flex-col p-2 sm:p-4"
		>
			<h2 class="text-4xl max-w-xl text-center mb-2 font-impact text-dark ">
				Harmonogram turnieju szachowego "Żółty Słoń
			</h2>
			<p class="text-2xl text-center font-bold mb-2 text-dark ">
				Turniej odbywa się co miesiąc, w pierwszą środę miesiąca.
			</p>
			<ListTournaments {tournamentData} />
		</div>
	</section> -->

	<!-- 
<section class="w-full pt-12 pb-12 h-auto">

</section> -->
</main>

<Footer {firstColumnData} {secondColumnData} {thirdColumnData} />

<style>
</style>
