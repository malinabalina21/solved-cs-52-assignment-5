Download Link: https://assignmentchef.com/product/solved-cs-52-assignment-5
<br>
<section id="cs-52-assignment-5" class="level1">

 <h1><span style="font-size: 2em;">Project 1 – Wallet</span></h1>

 <section id="project-1---wallet" class="level2">

  Following the class diagram shown below, create the class Wallet. A Wallet represents a carrier of bills and coins. You use your wallet to pay for things, which reduces the balance held inside. When you visit an ATM, you can fill it back up with cash again. A sample driver for this class is shown below. You should probably make a more thorough driver to test your class better. I will have my own driver which will aim to exploit any possible edge cases.




  <section id="wallet-class-description" class="level3">

   <h3>Wallet Class Description</h3>

   <pre class="cpp"><code>Wallet( );Wallet( int d, int c );int getDollars( );int getCents( );bool canPayFor( int dollarAmount, int centsAmount );void payFor( int dollarAmount, int changeAmount );void visitATMForCash( int dollarAmount );int dollars;int cents;</code></pre>

  </section>

  <section id="wallet-sample-driver-code" class="level3">

   <h3>Wallet Sample Driver Code</h3>

   <pre class="cpp"><code>int atm = 0, d = 0, c = 0, x = 0, y = 0;char cont = 'y';cout &lt;&lt; "Hello, how much money do you have in your wallet?" &lt;&lt; endl;cout &lt;&lt; "Dollars: ";cin &gt;&gt; d;cout &lt;&lt; "Cents: ";cin &gt;&gt; c;cout &lt;&lt; endl;Wallet w(d, c);cout &lt;&lt; "How many dollars would you like to withdraw from the ATM? ";cin &gt;&gt; atm;w.visitATMForCash(atm);cout &lt;&lt; "Currently you have: " &lt;&lt; endl;cout &lt;&lt; "Dollars: " &lt;&lt; w.getDollars() &lt;&lt; endl &lt;&lt; "Cents: " &lt;&lt; w.getCents() &lt;&lt; endl &lt;&lt; endl;do {  cout &lt;&lt; "How much are you going to spend?" &lt;&lt; endl;  cout &lt;&lt; "Dollars: ";  cin &gt;&gt; x;  cout &lt;&lt; "Cents: ";  cin &gt;&gt; y;  if (w.canPayFor(x, y) == true) {    w.payFor(x, y);    cout &lt;&lt; "
You now have: " &lt;&lt; endl;    cout &lt;&lt; "Dollars:" &lt;&lt; w.getDollars() &lt;&lt; endl &lt;&lt; "Cents:" &lt;&lt; w.getCents() &lt;&lt; endl;  }  else {    cout &lt;&lt; "
Sorry, you do not have enough money to spend. Please spend less." &lt;&lt; endl;  }  cout &lt;&lt; "Are you spending more money (y/n)? ";  cin &gt;&gt; cont;  cout &lt;&lt; endl;} while (cont == 'y');cout &lt;&lt; "You have this amount left in your wallet: " &lt;&lt; endl;cout &lt;&lt; "Dollars: " &lt;&lt; w.getDollars() &lt;&lt; " Cents: " &lt;&lt; w.getCents() &lt;&lt; endl &lt;&lt; endl;</code></pre>

   <section id="sample-driver-output" class="level4">

    <h4>Sample Driver Output</h4>

    <pre><code>Hello, how much money do you have in your wallet?Dollars:  10Cents:  0How many dollars would you like to withdraw from the ATM?  5Currently you have:Dollars: 15Cents: 0How much are you going to spend?Dollars:  6Cents:  56You now have:Dollars: 8Cents: 44Are you spending more money (y/n)?  yHow much are you going to spend?Dollars:  10Cents:  0Sorry, you do not have enough money to spend. Please spend less.Are you spending more money (y/n)?  nYou have this amount left in your wallet:Dollars: 8 Cents: 44</code></pre>

   </section>

  </section>

 </section>

</section>

<section id="codeboard-submission" class="level2">

 <h2>Codeboard Submission</h2>

 Please refer to the codeboard submission instructions here: <a href="http://mjedmonds.com/CS50/codeboard.html">http://mjedmonds.com/CS50/c</a>

</section>

<section id="cs-52-assignment-5" class="level1">

 <section id="project-2---record-player" class="level2">

  <h2></h2>

  <h2>Project 2 – Record Player</h2>

  Following the class diagram shown below, create the class <code>RecordPlayer</code>. An <code>RecordPlayer</code>represents a stereo component that can play vinyl records. Please review the class and the sample driver code. There is a specific order to the way the class methods should be called. In other words, you can’t plop the Needle unless there actually is a record on the player and the <code>recordplayer</code>is turned on. You also can’t return the Needle unless there is actually a record on the player and the <code>recordplayer</code>is turned on. Your class should enforce these rules and write errors to cout as they occur. A sample driver for this class is shown below.

  <section id="rules-of-the-record-player" class="level3">

   <h3>Rules of the record player</h3>

   <ol type="1">

    <li>You can affix a platter if the record player is on or off and the needle is not ploped</li>

    <li>Record player must be on and must have record affixed to the platter to plop the needle on the record</li>

    <li>Can only return the needle if the record player is on and there is a record on the player</li>

    <li>Performing the same action twice results in a “no-op” where nothing changes. For example, you can’t plop an already plopped needle, and you can’t return a needle that’s already returned. Another example: you can’t turn on/off a record player that is already on</li>

   </ol>

   <strong>Please note: codeboard must test differently for this project. There is no input. The provided driver will be called automatically. Your code will not compile when you start the project; only when you’ve implemented the RecordPlayer class will it compile successfully.</strong>

   <section id="record-player" class="level4">

    <h4>Record Player</h4>

    <pre class="cpp"><code>RecordPlayer( );void turnOn( );void turnOff( );bool isPoweredOn( );void affixPlatter( string record );void plopNeedle( );void returnNeedle( );bool isOn;string record;bool needleIsOnTheRecord;</code></pre>

   </section>

   <section id="record-player-sample-driver-code" class="level4">

    <h4>Record Player Sample Driver Code</h4>

    <pre class="cpp"><code>//declare 6 RecordPlayersRecordPlayer good_r, bad_r1, bad_r2, bad_r3, bad_r4, bad_r5;//first test correctgood_r.turnOn();good_r.affixPlatter("Barrow Manila I");good_r.plopNeedle();good_r.returnNeedle();good_r.turnOff();//bad test, plops needle without turning it on or putting record onbad_r1.plopNeedle();//turns it on but no record on platterbad_r2.turnOn();bad_r2.plopNeedle();//not on nor has album on platterbad_r3.returnNeedle();//turned on but no albumbad_r4.turnOn();bad_r4.returnNeedle();//not turned onbad_r5.affixPlatter("Barrow Manila I");bad_r5.plopNeedle();</code></pre>

   </section>

   <section id="record-player-sample-driver-code-output" class="level4">

    <h4>Record Player Sample Driver Code Output</h4>

    <pre><code>Record player is turned onRecord Barrow Manila I is now on the platterNeedle is placed on the recordNeedle is returned from the recordRecord player is turned offCannot place needle on the recordRecord player is turned onCannot place needle on the recordCannot return needle from the recordRecord player is turned onCannot return needle from the recordRecord Barrow Manila I is now on the platterCannot place needle on the record</code></pre>

   </section>

  </section>

 </section>

</section>

<section id="codeboard-submission" class="level2">

 <h2>Codeboard Submission</h2>

 Please refer to the codeboard submission instructions here: <a href="http://mjedmonds.com/CS50/codeboard.html">http://mjedmonds.com/CS50/codeboard.html</a>

</section>