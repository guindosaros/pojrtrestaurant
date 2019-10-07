# pojetrestaurant
### Bon moi pour le projet j'ai trouver 4 application
#### - Restaurant
#### - Reservation
#### - Messages
#### - Configuration


# Application Restaurant
l 'application restaurant sera l'application qui sera charger de gerer tous ceux qui est en rapport avec le restaurant
 - l'equipe 
 - le menu
 - les recettes 
 - les temoignage et autres 
 

* Categorie

```python

 class Categorie(models.Model):
    nom =  models.CharField(max_length=255)
    date_add =  models.DateTimeField(auto_now_add=True)
    date_update =  models.DateTimeField(auto_now=True)
    status =  models.BooleanField(default=True)
    def __str__(self):
        return self.nom
    
    class meta :
        verbose_name = "categorie"
        verbose_name_plural = "categorie"
```
 
 * Ingredient 
 
 ```python 
 class Ingrediant(models.Model):
    nom =  models.CharField(max_length=255)
    date_add =  models.DateTimeField(auto_now_add=True)
    date_update =  models.DateTimeField(auto_now=True)
    status =  models.BooleanField(default=True)
    
    def __str__(self):
        return self.nom
    
    class Meta:
        verbose_name = 'Ingrediant'
        verbose_name_plural = 'Ingrediant'
        
 ```
 * Menu 
 ```python
 class Menu(models.Model):
    categorie_id = models.ForeignKey(Categorie, on_delete=models.CASCADE,related_name="category_client")
    nom = models.CharField(max_length=160)
    prix = models.FloatField()
    ingrediant = models.ManyToManyField(Ingrediant,related_name="ingrediant_plat")
    image = models.ImageField(upload_to='image_plat')
    date_add =  models.DateTimeField(auto_now_add=True)
    date_update =  models.DateTimeField(auto_now=True)
    status =  models.BooleanField(default=True)
    def __str__(self):
         return self.nom

    class Meta:

        verbose_name = 'Menu'
        verbose_name_plural = 'Menu'
 ```
 
 * Poste
  ```python
  
  class Poste(models.Model):
    titre = models.CharField(max_length=160)
    date_add =  models.DateTimeField(auto_now_add=True)
    date_update =  models.DateTimeField(auto_now=True)
    status =  models.BooleanField(default=True)
    def __str__(self):
        return self.titre

    class Meta:
        verbose_name = 'Poste'
        verbose_name_plural = 'Postes'
   ```
   
   * Employer
   
   ```python
   class Cuisinier(models.Model):
    nom = models.CharField(max_length=160)
    prenom = models.CharField(max_length=160)
    photo = models.ImageField(upload_to='photo_cuisinier')
    poste = models.ForeignKey(Poste, on_delete=models.CASCADE,related_name="poste_cuisinier")
    twitter = models.URLField(max_length=200)
    facebook = models.URLField(max_length=200)
    google = models.URLField(max_length=200)
    instagram = models.URLField(max_length=200)
    date_add =  models.DateTimeField(auto_now_add=True)
    date_update =  models.DateTimeField(auto_now=True)
    status =  models.BooleanField(default=True)
 
    def __str__(self):
        return self.nom+ " " + self.prenom

    class Meta:
        verbose_name = 'Employer'
        verbose_name_plural = 'Employers'
    ```
