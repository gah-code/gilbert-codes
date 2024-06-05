##

```astro

import { useState } from 'react';
import { Link } from '@astrojs/router';
import logo from '../assets/french79-logo.png';
import blog from '../assets/nav-blog.png';
import github from '../assets/nav-github.png';

function slugify(string) {
return (
string &&
`${string}`
.match(
/[A-Z]{2,}(?=[A-Z][a-z]+[0-9]_|\b)|[A-Z]?[a-z]+[0-9]_|[A-Z]|[0-9]+/g
)
.map((x) => x.toLowerCase())
.join('-')
);
}

const mainNavItems = [
{ url: '/about', icon: blog, label: 'About me' },
{ url: '/projects', icon: blog, label: 'Projects' },
];

const socialNavItems = [
{ url: 'https://github.com/gah-code', icon: github, label: 'GitHub' },
];

const Navbar = () => {
const [show, setShow] = useState(false);
return (

<section className='navigation'>
<div className='container'>
<nav>
<Link to='/' className='item brand'>
<img src={logo} className='logo' alt='logo' />
<span>Gilbert A Haro</span>
</Link>

          {mainNavItems.map((item) => (
            <div className='nav-item-outer' key={item.label}>
              <img src={item.icon} alt={item.label} className='nav-image' />
              <Link
                to={item.url}
                activeClassName='active'
                className={`item ${slugify(item.label)}`}
              >
                <span>{item.label}</span>
              </Link>
            </div>
          ))}

          {socialNavItems.map((item) => (
            <div className='nav-item-outer' key={item.label}>
              <img src={item.icon} alt={item.label} className='nav-image' />
              <a
                href={item.url}
                className={`desktop-only item ${slugify(item.label)}`}
                target='_blank'
                rel='noreferrer'
              >
                <span>{item.label}</span>
              </a>
            </div>
          ))}
        </nav>
      </div>
    </section>

);
};

## export default Navbar;

<style lang="scss">
.navigation {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  z-index: 3;
  padding: 0.75rem 0;
  background: var(--navbar);
}

.navigation .container {
  display: flex;
}

.navigation a,
.navigation a:hover {
  text-decoration: none;
  background: transparent;
}

.navigation a.item.brand:hover {
  border-bottom-color: var(--rainbow-2);
}

.navigation .item.brand span,
.theme-toggle span {
  display: none;
}

.navigation .logo {
  height: 22px;
  width: 22px;
  min-height: 22px;
  min-width: 22px;
}

.navigation nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 0.25rem;
}

.navigation a.item,
.navigation button.item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 0.5rem;
  cursor: pointer;
  font-size: 0.9rem;
  font-weight: 500;
  color: rgba(255, 255, 255, 0.6);
  padding: 0;
  border: none;
  border-radius: 0;
  border-top: 2px solid transparent;
  border-bottom: 2px solid transparent;
  margin: 0 0.5rem;
}

.nav-item-outer {
  display: flex;
  align-items: center;
}

.nav-image {
  display: none;
  height: 22px;
  width: 22px;
  min-height: 22px;
  min-width: 22px;
}

.navigation a.brand {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  line-height: 1.2;
  font-size: 1.05rem;
  font-weight: 600;
  color: white;
  margin: 0 0.5rem 0 0.25rem;
  border-bottom: 2px solid transparent;
}

.navigation a.item:hover,
.navigation button.item:hover,
.navigation a.item.active,
.navigation button.item.active {
  color: white;
}

.navigation a.item.about-me:hover,
.navigation a.item.about-me.active {
  border-bottom-color: var(--rainbow-3);
}

.navigation a.item.writing:hover,
.navigation a.item.writing.active {
  border-bottom-color: var(--rainbow-4);
}

.navigation a.item.projects:hover,
.navigation a.item.projects.active {
  border-bottom-color: var(--rainbow-5);
}

.navigation a.item.git-hub:hover,
.navigation a.item.git-hub.active {
  border-bottom-color: var(--rainbow-1);
}

button.theme-toggle img {
  margin: 0;
}

button.theme-toggle {
  margin-left: auto;
  padding: 0.4rem 0.5rem;
  background: var(--gray-8);
  border-color: var(--gray-7);
  color: var(--gray-0);
}

button.theme-toggle:hover {
  background: var(--gray-7);
  border-color: var(--gray-6);
  color: white;
}

@media screen and (min-width: 850px) {
  button.theme-toggle img {
    margin-right: 0.25rem;
  }

  .nav-image {
    display: block;
  }

  .navigation .item.brand span,
  .theme-toggle span {
    display: block;
  }

  .navigation .logo {
    display: none;
    margin-right: 0;
  }

  .navigation a.brand {
    margin: 0 1.5rem 0 0.25rem;
  }

  .navigation nav {
    gap: 0.75rem;
  }
}
</style>

`
```
