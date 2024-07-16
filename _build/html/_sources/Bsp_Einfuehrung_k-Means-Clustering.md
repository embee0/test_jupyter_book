# Einführung in das k-Means-Clustering
(Dieser Text stammt von ChatGPT um zu testen, wie gut ich MyST-Markdown darin erzeugen kann.)

## Überblick

Das k-Means-Clustering ist ein beliebter unüberwachter Lernalgorithmus, der dazu verwendet wird, Datenpunkte in Gruppen oder Cluster zu unterteilen. Ziel ist es, die Daten so zu segmentieren, dass die Punkte innerhalb eines Clusters möglichst ähnlich und die Punkte zwischen den Clustern möglichst unterschiedlich sind.

```{note}
k-Means-Clustering wird häufig in Bereichen wie Marketing, Mustererkennung, Bildsegmentierung und vielen anderen angewendet.
```

## Algorithmus

Der k-Means-Algorithmus arbeitet in folgenden Schritten:

```{margin}
Der Wert von k muss im Voraus festgelegt werden und kann durch verschiedene Methoden wie das Elbow-Verfahren bestimmt werden.
```

1. **Initialisierung**: Wähle k Anfangszentren zufällig aus den Datenpunkten.
2. **Zuordnung**: Weise jeden Datenpunkt dem nächstgelegenen Zentrum zu.
3. **Aktualisierung**: Berechne die neuen Zentren als den Mittelwert der zugewiesenen Punkte.
4. Wiederhole Schritt 2 und 3, bis die Zentren sich nicht mehr signifikant ändern.


## Beispiel in Python

Im folgenden Beispiel werden wir den k-Means-Algorithmus auf einen einfachen Datensatz anwenden. Wir verwenden dazu die Bibliothek `scikit-learn`.

```{code} python
:label: my-program
:caption: Beispiel für einen Codeblock mit Überschrift
# Importiere notwendige Bibliotheken
import numpy as np
import matplotlib.pyplot as plt
from sklearn.cluster import KMeans
from sklearn.datasets import make_blobs

# Erzeuge einen Datensatz mit 3 Clustern
X, y = make_blobs(n_samples=300, centers=3, random_state=42)

# Führe k-Means-Clustering durch
kmeans = KMeans(n_clusters=3, random_state=42)
kmeans.fit(X)

# Vorhersagen
y_kmeans = kmeans.predict(X)

# Plot der Ergebnisse
plt.scatter(X[:, 0], X[:, 1], c=y_kmeans, s=50, cmap='viridis')
centers = kmeans.cluster_centers_
plt.scatter(centers[:, 0], centers[:, 1], c='red', s=200, alpha=0.75)
plt.title('k-Means Clustering')
plt.xlabel('Feature 1')
plt.ylabel('Feature 2')
plt.show()
```

## Übungsaufgaben

1. **Clusteranzahl bestimmen**:

   * Verwenden Sie das Elbow-Verfahren, um die optimale Anzahl von Clustern für einen gegebenen Datensatz zu bestimmen.
   * Erstellen Sie ein Diagramm, das den "Elbow" zeigt.

2. **Anwendung auf andere Datensätze**:

   * Wenden Sie den k-Means-Algorithmus auf einen anderen Datensatz Ihrer Wahl an (z.B. `Iris`\-Datensatz).
   * Visualisieren Sie die Ergebnisse und vergleichen Sie sie mit den tatsächlichen Labels (falls vorhanden).

3. **Vergleich mit anderen Clustering-Algorithmen**:

   * Vergleichen Sie k-Means mit einem anderen Clustering-Algorithmus wie DBSCAN oder hierarchischem Clustering.
   * Diskutieren Sie die Vor- und Nachteile der verschiedenen Methoden.

```{important}
Diese Aufgaben sollen Ihnen helfen, ein tieferes Verständnis für k-Means-Clustering zu entwickeln und dessen Anwendung in der Praxis zu üben.
```

## Fazit


```{margin}
Denken Sie daran, dass die Wahl des richtigen k-Werts und die Initialisierung der Clusterzentren die Ergebnisse stark beeinflussen können.
```

Das k-Means-Clustering ist ein mächtiges Werkzeug zur Segmentierung von Daten. Es ist wichtig, den richtigen Wert für k zu finden und die Ergebnisse sorgfältig zu interpretieren. Mit den oben genannten Übungen können Sie Ihre Fähigkeiten im Umgang mit diesem Algorithmus weiter vertiefen.
