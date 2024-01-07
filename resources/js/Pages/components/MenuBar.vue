<template>
    <aside :class="`${is_expanded ? 'is-expanded' : ''}`">
        <div class="logo">
            <Link><img :src="logo" alt="Logo" /></Link>
        </div>

        <div class="menu-toggle-wrap">
            <button class="menu-toggle" @click="ToggleMenu">
                <span class="material-icons">keyboard_double_arrow_right</span>
            </button>
        </div>

        <h3>Menu</h3>
        <div class="menu">
            <Link to="/" class="button">
            <span class="material-icons">home</span>
            <span class="text">Home</span>
            </Link>
            <span class="button-list" @click="ToggleMenu">
                <span class="button">
                    <span class="material-icons">description</span>
                    <span class="text">About</span>
                </span>
                <div :class="{ 'hide': !showElementsOfList }" >
                    <span class="button-list">
                        <Link to="/" class="button-list-iten">
                        <span class="text">Home</span>
                        </Link>
                        <Link to="/" class="button-list-iten">
                        <span class="text">Home</span>
                        </Link>
                        <Link to="/" class="button-list-iten">
                        <span class="text">Home</span>
                        </Link>
                    </span>
                </div>
            </span>
            <Link to="/team" class="button">
            <span class="material-icons">group</span>
            <span class="text">Team</span>
            </Link>
            <Link to="/contact" class="button">
            <span class="material-icons">email</span>
            <span class="text">Contact</span>
            </Link>
        </div>

        <div class="flex"></div>

        <div class="menu">
            <Link to="/settings" class="button">
            <span class="material-icons">settings</span>
            <span class="text">Settings</span>
            </Link>
        </div>
    </aside>
</template>

<script setup>
import { ref } from 'vue'
import logo from '/storage/app/public/logo.png'
import { Link } from '@inertiajs/vue3';

const is_expanded = ref(localStorage.getItem("is_expanded") === "true")
const showElementsOfList = ref(false);

const ToggleMenu = () => {
    is_expanded.value = !is_expanded.value
    localStorage.setItem("is_expanded", is_expanded.value)
    showElementsOfList.value = is_expanded.value;
}

</script>

<style lang="scss" scoped>
aside {
    display: flex;
    flex-direction: column;

    background-color: var(--dark);
    color: var(--light);

    width: calc(2rem + 32px);
    overflow: hidden;
    min-height: 100vh;
    padding: 1rem;

    transition: 0.2s ease-in-out;

    .flex {
        flex: 1 1 0%;
    }

    .hide {
        display: none;
    }

    .logo {
        margin-bottom: 1rem;

        img {
            width: 2rem;
        }
    }


    .menu-toggle-wrap {
        display: flex;
        justify-content: flex-end;
        margin-bottom: 1rem;

        position: relative;
        top: 0;
        transition: 0.2s ease-in-out;

        .menu-toggle {
            transition: 0.2s ease-in-out;

            .material-icons {
                font-size: 2rem;
                color: var(--light);
                transition: 0.2s ease-out;
            }

            &:hover {
                .material-icons {
                    color: var(--primary);
                    transform: translateX(0.5rem);
                }
            }
        }
    }

    h3,
    .button .text{
        opacity: 0;
        transition: opacity 0.3s ease-in-out;
    }

    h3 {
        color: var(--grey);
        font-size: 0.875rem;
        margin-bottom: 0.5rem;
        text-transform: uppercase;
    }

    .menu {
        margin: 0 -1rem;

        .button-list {
            display: flex;
            flex-direction: column;
            text-decoration: none;
            transition: 0.2s ease-in-out;

            .text {
                color: var(--light);
                transition: 0.2s ease-in-out;
            }

            .button-list-iten {
                display: flex;
                align-items: center;
                text-decoration: none;
                transition: 0.2s ease-in-out;
                padding: 0.9rem 2rem;

                .button-list-elements{
                    opacity: 0;
                    transition: opacity 0.3s ease-in-out;
                }

                .text {
                    color: var(--light);
                    transition: 0.2s ease-in-out;
                }

                &:hover {
                    background-color: var(--dark-alt);

                    .material-icons,
                    .text {
                        color: var(--primary);
                    }
                }

            }
        }

        .button {
            display: flex;
            align-items: center;
            text-decoration: none;
            transition: 0.2s ease-in-out;
            padding: 0.5rem 1rem;

            .material-icons {
                font-size: 2rem;
                color: var(--light);
                transition: 0.2s ease-in-out;
            }

            .text {
                color: var(--light);
                transition: 0.2s ease-in-out;
            }

            &:hover {
                background-color: var(--dark-alt);

                .material-icons,
                .text {
                    color: var(--primary);
                }
            }


        }
    }

    .footer {
        opacity: 0;
        transition: opacity 0.3s ease-in-out;

        p {
            font-size: 0.875rem;
            color: var(--grey);
        }
    }

    &.is-expanded {
        width: var(--sidebar-width);

        .menu-toggle-wrap {
            .menu-toggle {
                transform: rotate(-180deg);
            }
        }

        h3,
        .button .text {
            opacity: 1;
        }

        .button {
            .material-icons {
                margin-right: 1rem;
            }
        }

        .footer {
            opacity: 0;
        }
    }

    @media (max-width: 1024px) {
        position: absolute;
        z-index: 99;
    }
}
</style>