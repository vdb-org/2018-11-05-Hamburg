---
layout: workshop      # DON'T CHANGE THIS.
carpentry: "lc"    # what kind of Carpentry (must be either "lc" or "dc" or "swc")
venue: "SUB Hamburg"        # brief name of host site without address (e.g., "Euphoric State University")
address: "Raum AB003, Von-Melle-Park 3, 20146 Hamburg"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria")
country: "de"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1)
language: "de"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/ISO_639-1)
latlng: "53.56481,9.98516"       # decimal latitude and longitude of workshop venue (e.g., "41.7901128,-87.6007318" - use https://www.latlong.net/)
humandate: "5. - 6. Nov. 2018"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "FIXME"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2018-11-05      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2018-11-06        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: ["Dr. Katrin Leinweber", "FIXME"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: ["FIXME"]     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["fixme@example.org"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:             # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
  HEADER

  Edit the values in the block above to be appropriate for your workshop.
  If the value is not 'true', 'false', 'null', or a number, please use
  double quotation marks around the value, unless specified otherwise.
  And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}

<h4>This is the workshop template. Delete these lines and use it to customize your own website.
If you are running a self-organized workshop or have not put in a workshop request yet, please also fill in 
<a href="{{site.amy_site}}/submit">this workshop request form</a> to let us know about your workshop
and our administrator may contact you if we need any extra information.</h4>

<h2 id="general">Allgemeine Informationen</h2>

{% comment %}
  INTRODUCTION

  Edit the general explanatory paragraph below if you want to change
  the pitch.
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/intro.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/intro.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/intro.html %}
{% endif %}

{% comment %}
  AUDIENCE

  Explain who your audience is.  (In particular, tell readers if the
  workshop is only open to people from a particular institution.
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/who.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/who.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/who.html %}
{% endif %}

{% comment %}
  LOCATION

  This block displays the address and links to maps showing directions
  if the latitude and longitude of the workshop have been set.  You
  can use https://itouchmap.com/latlong.html to find the lat/long of an
  address.
{% endcomment %}
{% if page.latlng %}
<p id="where">
  <strong>Wo:</strong>
  {{page.address}}.
  Wegbeschreibung mit
  <a href="//www.openstreetmap.org/?mlat={{page.latlng | replace:',','&mlon='}}&zoom=16">OpenStreetMap</a>
  oder
  <a href="//maps.google.com/maps?q={{page.latlng}}">Google Maps</a>.
</p>
{% endif %}

{% comment %}
  DATE

  This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>Wann:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
  SPECIAL REQUIREMENTS

  Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Voraussetzungen:</strong> Die Teilnehmer*innen müssen einen Laptop mit einem Mac-, Linux- oder Windows-Betriebssystem (kein Tablett, Chromebook usw.) mitbringen, auf dem sie über Administratorrechte verfügen.
  Sie sollten einige spezielle Softwarepakete installiert haben (siehe <a href="#setup">unten</a>). 
  Sie sind außerdem verpflichtet, sich an den <a href="{{site.swc_site}}/conduct.html">Verhaltenskodex</a> von 
  {% if page.carpentry == "swc" %}
  Software Carpentry
  {% elsif page.carpentry == "dc" %}
  Data Carpentry
  {% elsif page.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  zu halten.
</p>

{% comment %}
  ACCESSIBILITY

  Modify the block below if there are any barriers to accessibility or
  special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Barrierefreiheit:</strong> Wir setzen uns dafür ein, diesen Workshop für alle zugänglich zu machen.
  Die Organisatoren des Workshops haben überprüft, dass:
</p>
<ul>
  <li>der Raum mit einem Rollstuhl erreichbar ist</li>
  <li>behindertengerechte Toiletten vorhanden sind</li>
</ul>
<p>
  Die Materialien werden im Vorfeld des Workshops zur Verfügung gestellt und bei Bedarf sind großformatige Handzettel nach vorheriger Anmeldung bei den Veranstaltern erhältlich.  Wenn wir Ihnen das Lernen erleichtern können (z.B. durch Gebärdensprachdolmetscher, Stillräume), setzen Sie sich bitte mit uns in Verbindung (Kontaktdaten siehe unten) und wir werden versuchen, Ihnen diese zur Verfügung zu stellen.
</p>

{% comment %}
  CONTACT EMAIL ADDRESS

  Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Kontakt</strong>:
  Bitte senden Sie eine E-Mail an
  {% if page.email %}
    {% for email in page.email %}
      {% if forloop.last and page.email.size > 1 %}
        or
      {% else %}
        {% unless forloop.first %}
        ,
        {% endunless %}
      {% endif %}
      <a href='mailto:{{email}}'>{{email}}</a>
    {% endfor %}
  {% else %}
    [wird noch bekannt gegeben]
  {% endif %}
  für weitere Informationen.
</p>

<hr/>

{% comment %} 
 SURVEYS - DO NOT EDIT SURVEY LINKS 
{% endcomment %}
<h2 id="surveys">Umfragen</h2>
<p>Bitte füllen Sie diese Umfragen vor und nach dem Workshop aus.</p>
{% if site.carpentry == "swc" %} 
<p><a href="{{ site.swc_pre_survey }}{{ site.github.project_title }}">Umfrage vor dem Workshop</a></p>
<p><a href="{{ site.swc_post_survey }}{{ site.github.project_title }}">Umfrage nach dem Workshop</a></p>
{% elsif site.carpentry == "dc" %}
<p><a href="{{ site.dc_pre_survey }}{{ site.github.project_title }}">Umfrage vor dem Workshop</a></p>
<p><a href="{{ site.dc_post_survey }}{{ site.github.project_title }}">Umfrage nach dem Workshop</a></p>
{% elsif site.carpentry == "lc" %}
<p><a href="{{ site.lc_pre_survey }}{{ site.github.project_title }}">Umfrage vor dem Workshop</a></p>
<p><a href="{{ site.lc_post_survey }}{{ site.github.project_title }}">Umfrage nach dem Workshop</a></p>
{% endif %}

<hr/>


{% comment %}
  SCHEDULE

  Show the workshop's schedule.  Edit the items and times in the table
  to match your plans.  You may also want to change 'Day 1' and 'Day
  2' to be actual dates or days of the week.
{% endcomment %}
<h2 id="schedule">Zeitplan</h2>

{% if page.carpentry == "swc" %}
  {% include sc/schedule.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/schedule.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/schedule.html %}
{% endif %}

{% comment %}
  Collaborative Notes

  If you want to use an Etherpad, go to

      http://pad.software-carpentry.org/YYYY-MM-DD-site

  where 'YYYY-MM-DD-site' is the identifier for your workshop,
  e.g., '2015-06-10-esu'.
{% endcomment %}
{% if page.collaborative_notes %}
<p id="collaborative_notes">
  Wir werden dieses <a href="{{page.collaborative_notes}}">kollaborative Dokument</a> zum Chatten, Notieren und Teilen von URLs und Code-Bits verwenden.
</p>
{% endif %}

<hr/>

{% comment %}
  SYLLABUS

  Show what topics will be covered.

  1. If your workshop is R rather than Python, remove the comment
     around that section and put a comment around the Python section.
  2. Some workshops will delete SQL.
  3. Please make sure the list of topics is synchronized with what you
     intend to teach.
  4. You may need to move the div's with class="col-md-6" around inside
     the div's with class="row" to balance the multi-column layout.

  This is one of the places where people frequently make mistakes, so
  please preview your site before committing, and make sure to run
  'tools/check' as well.
{% endcomment %}
<h2 id="syllabus">Syllabus</h2>

{% if page.carpentry == "swc" %}
  {% include sc/syllabus.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/syllabus.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/syllabus.html %}
{% endif %}

<hr/>

{% comment %}
  SETUP

  Delete irrelevant sections from the setup instructions.  Each
  section is inside a 'div' without any classes to make the beginning
  and end easier to find.

  This is the other place where people frequently make mistakes, so
  please preview your site before committing, and make sure to run
  'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  Um an einem
  {% if page.carpentry == "swc" %}
  Software Carpentry
  {% elsif page.carpentry == "dc" %}
  Data Carpentry
  {% elsif page.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  Workshop teilnehmen zu können, benötigen Sie Zugriff auf die unten beschriebene Software. Zusätzlich benötigen Sie einen aktuellen Webbrowser.
</p>
<p>
  Wir führen eine Liste der häufigsten Probleme, die während der Installation auftreten können, auf der
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Wiki-Seite Konfigurationsprobleme und Lösungen</a> (als Referenz für Instruktoren).
</p>

<div id="shell"> {% comment %} Start of 'shell' section. {% endcomment %}
  <h3>Die Bash-Shell</h3>

  <p>
    Bash ist eine häufig verwendete Shell, die Ihnen die Möglichkeit gibt, einfache Aufgaben schneller zu erledigen.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="shell-windows">Windows</h4>
      <a href="https://www.youtube.com/watch?v=339AEqk9c-8">Video Tutorial</a>
      <ol>
        <li>Laden Sie den <a href="https://git-for-windows.github.io/">Git for Windows Installer</a> herunter.</li>
        <li>Führen Sie das Installationsprogramm aus und befolgen Sie die folgenden Schritte:
          <ol>
            {% comment %} Git 2.18.0 Setup {% endcomment %}
            <li>
                Klicken Sie viermal auf "Weiter" (zweimal, wenn Sie zuvor Git installiert haben). Sie müssen in den Dialogfenstern "Informationen", "Standort", "Komponenten" und "Startmenü" nichts ändern.
            </li>
            <li>
                <strong>
                Wählen Sie "Standardmäßig den Nano-Editor verwenden" und klicken Sie auf "Weiter".
                </strong>
            </li>
            {% comment %} Adjusting your PATH environment {% endcomment %}
            <li>
                Lassen Sie "Git in der Windows-Eingabeaufforderung verwenden" ausgewählt und klicken Sie auf "Next". Wenn Sie dies vergessen, werden die Programme, die Sie für den Workshop benötigen, nicht richtig funktionieren. Führen Sie in diesem Fall den Installer erneut aus und wählen Sie die entsprechende Option.
            </li>
            {% comment %} Choosing the SSH executable {% endcomment %}
            <li>Klicken Sie auf "Weiter".</li>
            {% comment %} Configuring the line ending conversions {% endcomment %}
            <li>
                Lassen Sie "Auschecken im Windows-Stil, Zeilenenden im Unix-Stil übertragen" ausgewählt und klicken Sie auf "Weiter".
            </li>
            {% comment %} Configuring the terminal emulator to use with Git Bash {% endcomment %}
            <li>
              <strong>
                Wählen Sie "Standardkonsolenfenster von Windows verwenden" und klicken Sie auf "Weiter".
              </strong>
            </li>
            {% comment %} Configuring experimental performance tweaks {% endcomment %}
            <li>Klicken Sie auf "Installieren".</li>
            {% comment %} Installing {% endcomment %}
            {% comment %} Completing the Git Setup Wizard {% endcomment %}
            <li>Klicken Sie auf "Fertig stellen".</li>
          </ol>
        </li>
        <li>
          Wenn Ihre Umgebungsvariable "HOME" nicht gesetzt ist (oder Sie wissen nicht, was das ist):
          <ol>
            <li>Öffnen Sie die Eingabeaufforderung (Öffnen Sie das Startmenü, geben Sie cmd ein und drücken Sie [Enter]).</li>
            <li>
              Geben Sie die folgende Zeile genau so in das Eingabeaufforderungsfenster ein:
              <p><code>setx HOME "%USERPROFILE%"</code></p>
            </li>
            <li>Drücken Sie [Enter], Sie sollten folgendes sehen <code>SUCCESS: Specified value was saved.</code></li>
            <li>Beenden Sie die Eingabeaufforderung, indem Sie exit eingeben und dann [Enter] drücken.</li>
          </ol>
        </li>
      </ol>
      <p>Dadurch erhalten Sie sowohl Git als auch Bash (im Git Bash Programm).</p>
    </div>
    <div class="col-md-4">
      <h4 id="shell-macosx">macOS</h4>
      <p>
        Die Standard-Shell in allen Versionen von macOS ist Bash, es besteht also keine Notwendigkeit, etwas zu installieren. Sie erreichen Bash über das Terminal (zu finden unter <code>/Anwendungen/Dienstprogramme</code>). Im <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">Video-Tutorial</a> zur Git-Installation finden Sie ein Beispiel zum Öffnen des Terminals. Vielleicht möchten Sie das Terminal für diesen Workshop in Ihrem Dock behalten.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="shell-linux">Linux</h4>
      <p>
        Die Standard-Shell ist normalerweise Bash, aber wenn Ihre Maschine anders eingerichtet ist, können Sie sie ausführen, indem Sie ein Terminal öffnen und <code>bash</code> eingeben. Es besteht keine Notwendigkeit, etwas zu installieren.
      </p>
    </div>
  </div>
</div> {% comment %} End of 'shell' section. {% endcomment %}

<div id="git"> {% comment %} Start of 'Git' section. GitHub browser compatability
           is given at https://help.github.com/articles/supported-browsers/{% endcomment %}
  <h3>Git</h3>
  <p>
    Git ist ein Versionskontrollsystem, mit dem Sie verfolgen können, wer wann welche Änderungen vorgenommen hat, und mit dem Sie auf einfache Weise eine freigegebene oder öffentliche Version Ihres Codes auf <a href="https://github.com/">github.com</a> aktualisieren können. Sie benötigen einen <a href="https://help.github.com/articles/supported-browsers/">unterstützten</a> Webbrowser (aktuelle Versionen von Chrome, Firefox oder Safari, oder Internet Explorer Version 9 oder höher).
  </p>
  <p>
    Sie benötigen einen Account bei <a href="https://github.com/">github.com</a> für Teile der Git-Lektion. Einfache GitHub-Konten sind kostenlos. Wir empfehlen Ihnen, einen GitHub-Account zu erstellen, falls Sie noch keinen haben. Bitte bedenken Sie, welche persönlichen Informationen Sie preisgeben möchten. Zum Beispiel können Sie diese <a href="https://help.github.com/articles/keeping-your-email-address-private/">Anleitung</a> lesen, um Ihre E-Mail-Adresse bei GitHub geheim zu halten.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="git-windows">Windows</h4>
      <p>
        Git sollte als Teil der Bash-Installation (wie oben beschrieben) auf Ihrem Computer installiert werden.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="git-macosx">macOS</h4>
      <a href="https://www.youtube.com/watch?v=9LQhwETCdwY ">Video Tutorial</a>
      <p>
        <strong>Für OS X 10.9 und höher</strong> installieren Sie Git for Mac, indem Sie den neuesten "mavericks" Installer aus dieser <a href="http://sourceforge.net/projects/git-osx-installer/files/">Liste</a> herunterladen und ausführen. Da dieses Installationsprogramm nicht vom Entwickler signiert ist, müssen Sie möglicherweise mit der rechten Maustaste auf die .pkg-Datei klicken, auf Öffnen klicken und im Popup-Fenster auf Öffnen klicken. Nach der Installation von Git befindet sich nichts im Ordner <code>/Anwendungen</code>, da Git ein Kommandozeilenprogramm ist. Für ältere Versionen von OS X (10.5-10.8) verwenden Sie den neuesten verfügbaren Installer mit der Bezeichnung "snow-leopard".
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="git-linux">Linux</h4>
      <p>
        Wenn Git nicht bereits auf Ihrem Rechner vorhanden ist, können Sie versuchen, es über den Paketmanager Ihrer Distribution zu installieren. Für Debian/Ubuntu führen Sie <code>sudo apt-get install git</code> und für Fedora <code>sudo dnf install git</code> aus.
      </p>
    </div>
  </div>
</div> {% comment %} End of 'Git' section. {% endcomment %}

<div id="editor"> {% comment %} Start of 'editor' section. {% endcomment %}
  <h3>Text Editor</h3>

  <p>
    Wenn Sie Code schreiben, ist es schön, einen Texteditor zu haben, der für das Schreiben von Code optimiert ist, mit Funktionen wie der automatischen Farbcodierung von Schlüsselwörtern. Der Standardtext-Editor unter MacOS und Linux ist normalerweise auf Vim eingestellt, was nicht gerade für seine Intuitivität bekannt ist. Wenn Sie versehentlich darin stecken bleiben, versuchen Sie es mit der Escape-Taste, gefolgt von <code>:q!</code> (Doppelpunkt, Kleinbuchstabe 'q', Ausrufezeichen), und drücken Sie dann Return, um zur Shell zurückzukehren.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="editor-windows">Windows</h4>
      <p>
        nano ist ein Standard-Editor, der von den Instruktoren im Workshop verwendet wird. 
        Es wird zusammen mit Git installiert.
      </p>
      <p>
        Andere Editoren, die Sie verwenden können, sind <a href="https://notepad-plus-plus.org/">Notepad++</a> oder <a href="https://www.sublimetext.com/">Sublime Text</a>. Beachten Sie, dass Sie das Installationsverzeichnis zu Ihrem Systempfad hinzufügen müssen. Bitten Sie Ihren Trainer, Ihnen dabei zu helfen.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="editor-macosx">macOS</h4>
      <p>
        nano ist ein Standard-Editor, der von den Instruktoren im Workshop verwendet wird. 
        Im <a href="https://www.youtube.com/watch?v=9LQhwETCdwY">Video-Tutorial</a> zur Installation von Git finden Sie ein Beispiel zum Öffnen von nano. Es sollte vorinstalliert sein.
      </p>
      <p>
        Andere Editoren, die Sie verwenden können, sind <a href="https://www.barebones.com/products/textwrangler/">Text Wrangler</a> oder <a href="https://www.sublimetext.com/">Sublime Text</a>.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="editor-linux">Linux</h4>
      <p>
        nano ist ein Standard-Editor, der von den Instruktoren im Workshop verwendet wird.
        Es sollte vorinstalliert sein.
      </p>
      <p>
        Andere Editoren, die Sie verwenden können, sind <a href="https://wiki.gnome.org/Apps/Gedit">Gedit</a>, <a href="https://kate-editor.org/">Kate</a> oder <a href="https://www.sublimetext.com/">Sublime Text</a>.
      </p>
    </div>
  </div>
</div> {% comment %} End of 'editor' section. {% endcomment %}

<div id="openrefine"> {% comment %} Start of 'OpenRefine' section. {% endcomment %}
  <h3>OpenRefine</h3>
  <p>
    Für diese Lektion benötigen Sie OpenRefine und einen Webbrowser. <em>Hinweis:</em> OpenRefine ist ein Java-Programm, das auf Ihrem Rechner läuft (nicht in der Cloud). Es läuft innerhalb eines Webbrowsers, aber es wird keine Webverbindung benötigt.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="openrefine-windows">Windows</h4>
      <p>
        Überprüfen Sie, ob Sie entweder den Firefox- oder den Chrome-Browser installiert und als Standardbrowser eingestellt haben. <strong>OpenRefine läuft in Ihrem Standardbrowser.</strong> Es wird im Internet Explorer nicht korrekt ausgeführt.
      </p>
      <p>Laden Sie die Software von <a href="http://openrefine.org/">http://openrefine.org/</a> herunter.</p>
      <p>Erstellen Sie ein neues Verzeichnis namens OpenRefine.</p>
      <p>Entpacken Sie die heruntergeladene Datei in das OpenRefine-Verzeichnis, indem Sie mit der rechten Maustaste klicken und "Extrahieren...." wählen.</p>
      <p>Wechseln Sie in Ihr neu erstelltes OpenRefine-Verzeichnis.</p>
      <p>Starten Sie OpenRefine, indem Sie auf <code>google-refine.exe</code> klicken (dies öffnet ein Eingabeaufforderungsfenster, das Sie aber ignorieren können - warten Sie einfach, bis sich OpenRefine im Browser öffnet).</p>
      <p>Wenn Sie einen anderen Browser verwenden oder wenn OpenRefine nicht automatisch für Sie geöffnet wird, geben Sie in Ihrem Browser die Adresse <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> oder <a href="http://localhost:3333">http://localhost:3333</a>, um das Programm zu verwenden.</p>
    </div>
    <div class="col-md-4">
      <h4 id="openrefine-mac">Mac</h4>
      <p>Überprüfen Sie, ob Sie entweder den Firefox- oder den Chrome-Browser installiert und als Standardbrowser eingestellt haben. <strong>OpenRefine läuft in Ihrem Standardbrowser.</strong> Möglicherweise läuft es in Safari nicht richtig.</p>
      <p>Laden Sie die Software von <a href="http://openrefine.org/">http://openrefine.org/</a> herunter.</p>
      <p>Erstellen Sie ein neues Verzeichnis namens OpenRefine.</p>
      <p>Entpacken Sie die heruntergeladene Datei mit einem Doppelklick in das OpenRefine-Verzeichnis.</p>
      <p>Wechseln Sie in Ihr neu erstelltes OpenRefine-Verzeichnis.</p>
      <p>Starten Sie OpenRefine, indem Sie das Symbol in den Ordner Programme ziehen.</p>
      <p>Verwenden Sie <code>Strg-Klick/Öffnen ... </code>, um es zu starten.</p>
      <p>Wenn Sie einen anderen Browser verwenden oder wenn OpenRefine nicht automatisch für Sie geöffnet wird, geben Sie in Ihrem Browser die Adresse <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> oder <a href="http://localhost:3333">http://localhost:3333</a>, um das Programm zu verwenden.</p>
    </div>
    <div class="col-md-4">
      <h4 id="openrefine-linux">Linux</h4>
      <p>Überprüfen Sie, ob Sie entweder den Firefox- oder den Chrome-Browser installiert und als Standardbrowser eingestellt haben. <strong>OpenRefine läuft in Ihrem Standardbrowser.</strong></p>
      <p>Laden Sie die Software von <a href="http://openrefine.org/">http://openrefine.org/</a> herunter.</p>
      <p>Erstellen Sie ein neues Verzeichnis namens OpenRefine.</p>
      <p>Entpacken Sie die heruntergeladene Datei in das OpenRefine-Verzeichnis.</p>
      <p>Wechseln Sie in Ihr neu erstelltes OpenRefine-Verzeichnis.</p>
      <p>Starten Sie OpenRefine, indem Sie <code>./refine</code> in das Terminal im OpenRefine-Verzeichnis eingeben.</p>
      <p>Wenn Sie einen anderen Browser verwenden oder wenn OpenRefine nicht automatisch für Sie geöffnet wird, geben Sie in Ihrem Browser die Adresse <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> oder <a href="http://localhost:3333">http://localhost:3333</a>, um das Programm zu verwenden.</p>
    </div>
  </div>
</div> {% comment %} End of 'OpenRefine' section. {% endcomment %}

{% comment %}
<div id="vm">
  <h3>Virtual Machine</h3>

  <p>
    Some instructors prefer to have learners use a virtual machine (VM)
    rather than install software on their own computers.  If your
    instructors have chosen to do this, please:
  </p>
  <ol>
    <li>
      Install <a href="https://www.virtualbox.org/">VirtualBox</a>.
    </li>
    <li>
      Download our <a href="{{site.swc_vm}}">VM image</a>.
      <strong>Warning:</strong> this file is 1.7 GByte, so please
      download it <em>before</em> coming to your workshop.
    </li>
    <li>
      Load the VM into VirtualBox by selecting "Import Appliance" and
      loading the <code>.ova</code> file.
    </li>
  </ol>
</div>
{% endcomment %}
