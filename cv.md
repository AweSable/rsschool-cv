**Denis Poryvaev**
Phone: +79811281075
E-mail: DA.Poryvaev@gmail.com
Моя цель - преодолеть тот барьер, который мешает мне в полной мере освоить программирование, проникнуться этой способностью к трансформации идеи в программный продукт.
Приоритетом для меня является самосовершенствование и взаимовыручка при работе в коллективе.
Моей сильной стороной является стремление в любой задаче найти лучшее решение и исполнительность.
Мой опыт работы составляет 4 года работы на АвтоВАЗе в качестве технолога по сборке шасси и 5 лет работы технологом на тихвинском вагоностроительном заводе в качестве технолога по изготовлению стальных гнутых профилей. В настоящий момент занимаю должность ведущего инженера-технолога.
В своей работе я часто использую программы, написанные на VBA или Python для автоматизации рутинных задач. Самым большим личным проектом является база данных в MS Access с возможностью автоматически обновлять данные из файлов Excel, применением множественных фильтров и просмотром связанной информации (маршруты изготовления, спецификация, карты раскроя, ссылки на чертежи) в одном окне.
Программирование в настоящий момент является для меня хобби, и я стремлюсь перейти в эту область полностью, т.к. это то, что мне по настоящему нравится.
В настоящий момент я знаю синтаксис и могу немного программировать на: VBA, Python и C++.
Ниже приведён пример кода на Python, сохраняющий ссылки на чертежи в текстовом файле для последующего импорта в базу данных MS Access.
<pre><code>import os, re
def saveSubdir(directory, file):
	dir=directory
	myfile=file
	regWasteDoc=re.compile(' ВП[ ,_]|ПСИ| РЭ[ ,_]| ГЧ[ ,_]| Д\d\d?[ ,_]| РР\d\d?[ ,_]| ГЧ[ ,_]| ПМ[ ,_]|[П,п]огашенн?ые|[А,а]нн?лированн?ые|[З,з]амен[е,ё]нн?ые')
	regPartIndexVar1=re.compile('^ЦДЛР[ ,\.](\d\d\d\d\.\d\d\.\d\d\.\d\d\d*).+')
	regPartIndexVar2=re.compile('^(\d\d\d\d\.\d\d\.\d\d\.\d\d\d).+')
	regPartIndexVar3=re.compile('^(\d\d\d\d\-\d\d\.\d\d\.\d\d\.\d\d\d).+')
	MatchVar1=False
	MatchVar2=False
	MatchVar3=False
	for (thisDir, SubHere, filesHere) in os.walk(dir):
		for filename in filesHere:
			MatchWasteDoc=regWasteDoc.search(filename)
			MatchVar1=regPartIndexVar1.search(filename)
			MatchVar2=regPartIndexVar2.search(filename)
			MatchVar3=regPartIndexVar3.search(filename)
			Bol=MatchVar1 or MatchVar2 or MatchVar3
			if MatchWasteDoc==None and Bol:
				if regPartIndexVar1.search(filename):
					matchPartIndex=regPartIndexVar1.match(filename)
					sPartIndex=matchPartIndex.group(1)
				elif regPartIndexVar2.search(filename):
					matchPartIndex=regPartIndexVar2.match(filename)
					sPartIndex=matchPartIndex.group(1)
				elif regPartIndexVar3.search(filename):
					matchPartIndex=regPartIndexVar3.match(filename)
					sPartIndex=matchPartIndex.group(1)
				ref='@#'+os.path.join(thisDir, filename)+'#'
				record=ref+';'+filename[:-4]+';'+thisDir+';'+sPartIndex+'\n'
				myfile.write(record.encode())
			MatchVar1=False
			MatchVar2=False
			MatchVar3=False
	
drawingdirs = []
drawingdirs.insert(0,r'R:\Специальные документы\Архив КД продукта')
drawingdirs.insert(1,r'R:\Специальные документы\ТСМ Архив КД продукта')
drawingdirs.insert(2,r'R:\Специальные документы\ТХМ Архив КД продукта')
drawingdirs.insert(3,r'R:\Специальные документы\Проекты извещений')

myfile = open(r'D:\Резка\БД\references.txt', 'wb')
for	dir in drawingdirs:
	saveSubdir(dir, myfile)
myfile.close()

sketchesdir=r'R:\Специальные документы\Карты эскизов к ТП заготовительного производства'
myfile = open(r'D:\Резка\БД\referencesSketches.txt', 'wb')
saveSubdir(sketchesdir, myfile)
myfile.close()</code></pre>
**Work experience**

**Education**
Higher
2009	**Samara university, Samara**
	Faculty of Aircraft Engines, Internal combustion engines
**Knowledge of languages**
English — A1 — Beginner
