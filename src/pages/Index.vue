<template>
    <main class="page-content">
        <Slider :slides="slides" :sliderOptions="sliderOptions" />
        <section> 
            <h2>How to replace the front brake pads</h2>  

            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eos, voluptate. Mollitia tenetur, minima quisquam consectetur necessitatibus laudantium beatae nulla quos? Et iusto voluptas, voluptatum nemo delectus distinctio deserunt facilis sint.</p>
            <p>Ipsum soluta iusto minima error maxime inventore consequuntur assumenda debitis doloremque, aperiam obcaecati? Laudantium, illo. Hic, quas magnam expedita aliquam, atque nulla voluptatum odio quidem maiores maxime, error alias iure.</p>
        </section>
    </main>
</template>

<script>
import Slider from '@/components/Slider/Slider.vue'; 

export default {
    data() {
        return {
            sliderOptions: {
                autoStart: true,
                animationDuration: 5000,
            },
            slides: [
                {
                    title: 'How to replace the \n\n**front brake pads**' ,
                    subtitle:'Perform the replacement of brake pads in complete set for each axis. This provides effective braking. Do not wash the brake elements with gasoline, diesel fuel or gasoline-based solvents. Observe the safety procedures! when brake pads work, brake dust is formed. Therefore, do not use compressed air and do not...',
                    link: {
                        src: 'https://facebook.com',
                        title: "Replace the front brake"
                    },
                    image: require('../assets/images/audi.jpg'),
                    tabTitle: "Brake replacing"
                },
                {
                    title: '**Driver Shift Control:** \n\nfeatures, advantages & \n\ndisadvantages',
                    subtitle:'Driver Shift Control (DSC) is the manual shift function in automatic transmission of Pontanic, Chevrolet, Cadillac, and Buick cars. It allows maximum driving smoothness and helps to save fuel. This system allows engine braking and improves the vehicles dynamics and manoeuvrability.',
                    link: {
                        src: 'https://facebook.com',
                        title: "How it works"
                    },
                    image: require('../assets/images/ford.jpg'),
                    tabTitle: "Driver Shift Control"
                },
                {
                    title: 'What is **Sportmatic?**',
                    subtitle:'Sportmatic is a function of manual shifting in automatic transmission installed on Kia cars. it is offered either as a factory-installed equipment or as an option for most current versions. it has been in use since 2001. This function improves the vechicle performance compared to a classic automatic transmission.',
                    link: {
                        src: 'https://facebook.com',
                        title: "Operating principle"
                    },
                    image: require('../assets/images/msds.jpg'),
                    tabTitle: "Sportmatic"
                },
                {
                    title: '**Suplemental** \n\nRestraint System',
                    subtitle:'Sportmatic is a function of manual shifting in automatic transmission installed on Kia cars. it is offered either as a factory-installed equipment or as an option for most current versions. it has been in use since 2001. This function improves the vechicle performance compared to a classic automatic transmission.',
                    link: {
                        src: 'https://facebook.com',
                        title: "Operating principle"
                    },
                    image: require('../assets/images/ferrari.jpg'),
                    tabTitle: "Suplemental Restraint System",
                },
            ]
        }
    },
    components: {
        Slider,
    }
}
</script>

<style scoped>

</style>