`schedule <https://schedule.readthedocs.io/>`__
===============================================


.. image:: https://github.com/dbader/schedule/workflows/Tests/badge.svg
        :target: https://github.com/dbader/schedule/actions?query=workflow%3ATests+branch%3Amaster

.. image:: https://coveralls.io/repos/dbader/schedule/badge.svg?branch=master
        :target: https://coveralls.io/r/dbader/schedule

.. image:: https://img.shields.io/pypi/v/schedule.svg
        :target: https://pypi.python.org/pypi/schedule

Python job scheduling for humans. Run Python functions (or any other callable) periodically using a friendly syntax.

- A simple to use API for scheduling jobs, made for humans.
- In-process scheduler for periodic jobs. No extra processes needed!
- Very lightweight and no external dependencies.
- Excellent test coverage.
- Tested on Python and 3.6, 3.7, 3.8, 3.9

Usage
-----

.. code-block:: bash

    $ git clone https://github.com/usunyu/async-schedule

.. code-block:: python

    from schedule import async_schedule
    import asyncio

    async def job():
        await asyncio.sleep(1.0)
        print("I'm working...")
    
    async_schedule.every(10).seconds.do(job)
    async_schedule.every(10).minutes.do(job)
    async_schedule.every().hour.do(job)
    async_schedule.every().day.at("10:30").do(job)
    async_schedule.every(5).to(10).minutes.do(job)
    async_schedule.every().monday.do(job)
    async_schedule.every().wednesday.at("13:15").do(job)
    async_schedule.every().day.at("12:42", "Europe/Amsterdam").do(job)
    async_schedule.every().minute.at(":17").do(job)

    async def job_with_argument(name):
        await asyncio.sleep(1.0)
        print(f"I am {name}")
        
    async_schedule.every(10).seconds.do(job_with_argument, name="Peter")
        
    async def main():
        while True:
            await async_schedule.run_pending()
            await asyncio.sleep(1.0)

    asyncio.run(main())

Documentation
-------------

Schedule's documentation lives at `schedule.readthedocs.io <https://schedule.readthedocs.io/>`_.


Meta
----

Daniel Bader - `@dbader_org <https://twitter.com/dbader_org>`_ - mail@dbader.org

Inspired by `Adam Wiggins' <https://github.com/adamwiggins>`_ article `"Rethinking Cron" <https://adam.herokuapp.com/past/2010/4/13/rethinking_cron/>`_ and the `clockwork <https://github.com/Rykian/clockwork>`_ Ruby module.

Distributed under the MIT license. See `LICENSE.txt <https://github.com/dbader/schedule/blob/master/LICENSE.txt>`_ for more information.

https://github.com/dbader/schedule
