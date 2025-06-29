"use client"

import { useState } from "react"
import { Button } from "@/components/ui/button"
import { Card, CardContent } from "@/components/ui/card"
import { Input } from "@/components/ui/input"
import { Label } from "@/components/ui/label"
import { Select, SelectContent, SelectItem, SelectTrigger, SelectValue } from "@/components/ui/select"
import { Sheet, SheetContent, SheetTrigger } from "@/components/ui/sheet"
import { Badge } from "@/components/ui/badge"
import { ShoppingCart, User, Settings, Menu, Plus, Star, Heart, Trash2 } from "lucide-react"
import Image from "next/image"

// Floating Logo Component
function FloatingLogo({ size = 48, className = "" }: { size?: number; className?: string }) {
  const [isHovered, setIsHovered] = useState(false)

  return (
    <div
      className={`perspective-1000 ${className}`}
      onMouseEnter={() => setIsHovered(true)}
      onMouseLeave={() => setIsHovered(false)}
    >
      <div
        className={`
          relative transition-all duration-300 ease-in-out
          ${isHovered ? "transform rotate-y-15 rotate-x-5 scale-110" : "animate-bounce"}
        `}
        style={{ width: size, height: size }}
      >
        <div
          className={`
            relative bg-gradient-to-br from-white via-gray-100 to-gray-200 
            rounded-xl flex items-center justify-center p-2
            shadow-2xl border border-gray-200 transition-all duration-300
          `}
          style={{
            width: size,
            height: size,
            boxShadow: isHovered
              ? "0 20px 40px rgba(147, 51, 234, 0.4), 0 0 30px rgba(147, 51, 234, 0.3)"
              : "0 10px 25px rgba(0, 0, 0, 0.2), 0 5px 15px rgba(0, 0, 0, 0.1)",
          }}
        >
          <div
            className="w-full h-full bg-purple-600 rounded-lg flex items-center justify-center text-white font-bold text-xl"
            style={{ fontSize: size * 0.3 }}
          >
            BZ
          </div>
          {isHovered && (
            <>
              <div className="absolute -top-2 -right-2 w-2 h-2 bg-purple-400 rounded-full animate-ping" />
              <div className="absolute -bottom-2 -left-2 w-1.5 h-1.5 bg-blue-400 rounded-full animate-ping" />
              <div className="absolute top-1/2 -right-3 w-1 h-1 bg-pink-400 rounded-full animate-ping" />
            </>
          )}
        </div>
      </div>
    </div>
  )
}

// Navigation Component
function Navigation() {
  const [open, setOpen] = useState(false)
  const navItems = [
    { name: "Home", href: "/" },
    { name: "Men's", href: "#mens" },
    { name: "Women's", href: "#womens" },
    { name: "Accessories", href: "#accessories" },
    { name: "Custom", href: "#customize" },
    { name: "About", href: "#about" },
    { name: "Contact", href: "#contact" },
  ]

  return (
    <nav className="border-b border-gray-800">
      <div className="container mx-auto px-4">
        <div className="hidden md:flex items-center justify-center space-x-8 py-4">
          {navItems.map((item) => (
            <a
              key={item.name}
              href={item.href}
              className="text-gray-300 hover:text-white transition-colors font-medium"
            >
              {item.name}
            </a>
          ))}
        </div>
        <div className="md:hidden py-4">
          <Sheet open={open} onOpenChange={setOpen}>
            <SheetTrigger asChild>
              <Button variant="ghost" size="icon" className="text-white">
                <Menu className="h-6 w-6" />
              </Button>
            </SheetTrigger>
            <SheetContent side="right" className="bg-black border-gray-800">
              <nav className="flex flex-col space-y-4 mt-8">
                {navItems.map((item) => (
                  <a
                    key={item.name}
                    href={item.href}
                    className="text-gray-300 hover:text-white transition-colors py-2 font-medium"
                    onClick={() => setOpen(false)}
                  >
                    {item.name}
                  </a>
                ))}
              </nav>
            </SheetContent>
          </Sheet>
        </div>
      </div>
    </nav>
  )
}

// Admin Panel Component
function AdminPanel() {
  const [products, setProducts] = useState([
    { id: 1, name: "Premium Hoodie", price: 89, stock: 15, category: "Men's" },
    { id: 2, name: "Designer Jeans", price: 129, stock: 8, category: "Men's" },
    { id: 3, name: "Elegant Dress", price: 159, stock: 12, category: "Women's" },
  ])

  const [newProduct, setNewProduct] = useState({
    name: "",
    price: "",
    stock: "",
    category: "Men's",
  })

  const addProduct = () => {
    if (newProduct.name && newProduct.price && newProduct.stock) {
      setProducts([
        ...products,
        {
          id: Date.now(),
          name: newProduct.name,
          price: Number.parseInt(newProduct.price),
          stock: Number.parseInt(newProduct.stock),
          category: newProduct.category,
        },
      ])
      setNewProduct({ name: "", price: "", stock: "", category: "Men's" })
    }
  }

  const deleteProduct = (id: number) => {
    setProducts(products.filter((p) => p.id !== id))
  }

  return (
    <div className="bg-gray-900 border-b border-gray-800">
      <div className="container mx-auto px-4 py-8">
        <h3 className="text-2xl font-bold text-white mb-6">Admin Panel - Stock Management</h3>

        <div className="grid grid-cols-1 lg:grid-cols-2 gap-8">
          <Card className="bg-gray-800 border-gray-700">
            <CardContent className="p-6">
              <h4 className="text-lg font-semibold text-white mb-4">Add New Product</h4>
              <div className="space-y-4">
                <div>
                  <Label htmlFor="name" className="text-gray-300">
                    Product Name
                  </Label>
                  <Input
                    id="name"
                    value={newProduct.name}
                    onChange={(e) => setNewProduct({ ...newProduct, name: e.target.value })}
                    className="bg-gray-700 border-gray-600 text-white"
                  />
                </div>
                <div>
                  <Label htmlFor="price" className="text-gray-300">
                    Price ($)
                  </Label>
                  <Input
                    id="price"
                    type="number"
                    value={newProduct.price}
                    onChange={(e) => setNewProduct({ ...newProduct, price: e.target.value })}
                    className="bg-gray-700 border-gray-600 text-white"
                  />
                </div>
                <div>
                  <Label htmlFor="stock" className="text-gray-300">
                    Stock Quantity
                  </Label>
                  <Input
                    id="stock"
                    type="number"
                    value={newProduct.stock}
                    onChange={(e) => setNewProduct({ ...newProduct, stock: e.target.value })}
                    className="bg-gray-700 border-gray-600 text-white"
                  />
                </div>
                <div>
                  <Label htmlFor="category" className="text-gray-300">
                    Category
                  </Label>
                  <Select
                    value={newProduct.category}
                    onValueChange={(value) => setNewProduct({ ...newProduct, category: value })}
                  >
                    <SelectTrigger className="bg-gray-700 border-gray-600 text-white">
                      <SelectValue />
                    </SelectTrigger>
                    <SelectContent className="bg-gray-700 border-gray-600">
                      <SelectItem value="Men's">Men's</SelectItem>
                      <SelectItem value="Women's">Women's</SelectItem>
                      <SelectItem value="Accessories">Accessories</SelectItem>
                    </SelectContent>
                  </Select>
                </div>
                <Button onClick={addProduct} className="w-full bg-purple-600 hover:bg-purple-700">
                  <Plus className="w-4 h-4 mr-2" />
                  Add Product
                </Button>
              </div>
            </CardContent>
          </Card>

          <Card className="bg-gray-800 border-gray-700">
            <CardContent className="p-6">
              <h4 className="text-lg font-semibold text-white mb-4">Current Inventory</h4>
              <div className="space-y-3 max-h-96 overflow-y-auto">
                {products.map((product) => (
                  <div key={product.id} className="flex items-center justify-between p-3 bg-gray-700 rounded-lg">
                    <div>
                      <h5 className="font-medium text-white">{product.name}</h5>
                      <p className="text-sm text-gray-300">
                        ${product.price} • {product.category}
                      </p>
                      <Badge variant={product.stock > 10 ? "default" : product.stock > 5 ? "secondary" : "destructive"}>
                        Stock: {product.stock}
                      </Badge>
                    </div>
                    <Button variant="destructive" size="sm" onClick={() => deleteProduct(product.id)}>
                      <Trash2 className="w-4 h-4" />
                    </Button>
                  </div>
                ))}
              </div>
            </CardContent>
          </Card>
        </div>
      </div>
    </div>
  )
}

// Product Grid Component
function ProductGrid() {
  const [cart, setCart] = useState<{ id: number; name: string; price: number; quantity: number }[]>([])

  const products = [
    {
      id: 1,
      name: "Premium Black Hoodie",
      price: 89,
      image: "/placeholder.svg?height=300&width=300",
      rating: 4.8,
      reviews: 124,
    },
    {
      id: 2,
      name: "Designer Denim Jacket",
      price: 129,
      image: "/placeholder.svg?height=300&width=300",
      rating: 4.9,
      reviews: 89,
    },
    {
      id: 3,
      name: "Luxury Sneakers",
      price: 199,
      image: "/placeholder.svg?height=300&width=300",
      rating: 4.7,
      reviews: 156,
    },
    {
      id: 4,
      name: "Elegant Evening Dress",
      price: 159,
      image: "/placeholder.svg?height=300&width=300",
      rating: 4.9,
      reviews: 78,
    },
    {
      id: 5,
      name: "Casual Summer Shirt",
      price: 49,
      image: "/placeholder.svg?height=300&width=300",
      rating: 4.6,
      reviews: 203,
    },
    {
      id: 6,
      name: "Premium Leather Bag",
      price: 249,
      image: "/placeholder.svg?height=300&width=300",
      rating: 4.8,
      reviews: 92,
    },
    {
      id: 7,
      name: "Stylish Sunglasses",
      price: 79,
      image: "/placeholder.svg?height=300&width=300",
      rating: 4.5,
      reviews: 167,
    },
    {
      id: 8,
      name: "Cozy Winter Scarf",
      price: 39,
      image: "/placeholder.svg?height=300&width=300",
      rating: 4.7,
      reviews: 134,
    },
  ]

  const addToCart = (product: (typeof products)[0]) => {
    setCart((prev) => {
      const existing = prev.find((item) => item.id === product.id)
      if (existing) {
        return prev.map((item) => (item.id === product.id ? { ...item, quantity: item.quantity + 1 } : item))
      }
      return [...prev, { id: product.id, name: product.name, price: product.price, quantity: 1 }]
    })
  }

  return (
    <div className="py-16">
      <div className="container mx-auto px-4">
        <div className="text-center mb-12">
          <h2 className="text-4xl font-bold text-white mb-4">Featured Collections</h2>
          <p className="text-gray-400 text-lg">Discover our latest premium clothing and accessories</p>
        </div>

        <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          {products.map((product) => (
            <Card
              key={product.id}
              className="bg-gray-900 border-gray-800 overflow-hidden group hover:border-purple-500 transition-all duration-300"
            >
              <div className="relative overflow-hidden">
                <Image
                  src={product.image || "/placeholder.svg"}
                  alt={product.name}
                  width={300}
                  height={300}
                  className="w-full h-64 object-cover group-hover:scale-105 transition-transform duration-300"
                />
                <div className="absolute top-4 right-4">
                  <Button size="icon" variant="ghost" className="bg-black/50 hover:bg-black/70 text-white">
                    <Heart className="w-4 h-4" />
                  </Button>
                </div>
              </div>
              <CardContent className="p-6">
                <h3 className="font-semibold text-white mb-2">{product.name}</h3>
                <div className="flex items-center mb-3">
                  <div className="flex items-center">
                    {[...Array(5)].map((_, i) => (
                      <Star
                        key={i}
                        className={`w-4 h-4 ${
                          i < Math.floor(product.rating) ? "text-yellow-400 fill-current" : "text-gray-600"
                        }`}
                      />
                    ))}
                  </div>
                  <span className="text-sm text-gray-400 ml-2">({product.reviews})</span>
                </div>
                <div className="flex items-center justify-between">
                  <span className="text-2xl font-bold text-purple-400">${product.price}</span>
                  <Button onClick={() => addToCart(product)} className="bg-purple-600 hover:bg-purple-700 text-white">
                    <ShoppingCart className="w-4 h-4 mr-2" />
                    Add to Cart
                  </Button>
                </div>
              </CardContent>
            </Card>
          ))}
        </div>
      </div>
    </div>
  )
}

// Outfit Customizer Component
function OutfitCustomizer() {
  const [selectedItems, setSelectedItems] = useState({
    top: null as any,
    bottom: null as any,
    shoes: null as any,
    accessories: null as any,
  })

  const customizationOptions = {
    top: [
      { id: 1, name: "Classic T-Shirt", price: 29, color: "White" },
      { id: 2, name: "Premium Hoodie", price: 79, color: "Black" },
      { id: 3, name: "Designer Polo", price: 59, color: "Navy" },
    ],
    bottom: [
      { id: 1, name: "Slim Jeans", price: 89, color: "Blue" },
      { id: 2, name: "Cargo Pants", price: 99, color: "Khaki" },
      { id: 3, name: "Chino Shorts", price: 49, color: "Beige" },
    ],
    shoes: [
      { id: 1, name: "Sneakers", price: 129, color: "White" },
      { id: 2, name: "Boots", price: 189, color: "Brown" },
      { id: 3, name: "Loafers", price: 159, color: "Black" },
    ],
    accessories: [
      { id: 1, name: "Watch", price: 199, color: "Silver" },
      { id: 2, name: "Sunglasses", price: 89, color: "Black" },
      { id: 3, name: "Belt", price: 59, color: "Leather" },
    ],
  }

  const totalPrice = Object.values(selectedItems).reduce((sum, item) => sum + (item?.price || 0), 0)

  return (
    <div className="py-16 bg-gray-900">
      <div className="container mx-auto px-4">
        <div className="text-center mb-12">
          <h2 className="text-4xl font-bold text-white mb-4">Custom Outfit Builder</h2>
          <p className="text-gray-400 text-lg">Create your perfect look with our customization tools</p>
        </div>

        <div className="grid grid-cols-1 lg:grid-cols-2 gap-12">
          <div className="space-y-8">
            {Object.entries(customizationOptions).map(([category, items]) => (
              <Card key={category} className="bg-gray-800 border-gray-700">
                <CardContent className="p-6">
                  <h3 className="text-xl font-semibold text-white mb-4 capitalize">{category}</h3>
                  <div className="grid grid-cols-1 gap-3">
                    {items.map((item) => (
                      <div
                        key={item.id}
                        className={`p-4 rounded-lg border cursor-pointer transition-all ${
                          selectedItems[category as keyof typeof selectedItems]?.id === item.id
                            ? "border-purple-500 bg-purple-500/10"
                            : "border-gray-600 hover:border-gray-500"
                        }`}
                        onClick={() => setSelectedItems((prev) => ({ ...prev, [category]: item }))}
                      >
                        <div className="flex justify-between items-center">
                          <div>
                            <h4 className="font-medium text-white">{item.name}</h4>
                            <p className="text-sm text-gray-400">{item.color}</p>
                          </div>
                          <span className="text-purple-400 font-semibold">${item.price}</span>
                        </div>
                      </div>
                    ))}
                  </div>
                </CardContent>
              </Card>
            ))}
          </div>

          <div className="lg:sticky lg:top-8">
            <Card className="bg-gray-800 border-gray-700">
              <CardContent className="p-6">
                <h3 className="text-xl font-semibold text-white mb-6">Your Custom Outfit</h3>

                <div className="space-y-4 mb-6">
                  {Object.entries(selectedItems).map(([category, item]) => (
                    <div key={category} className="flex justify-between items-center py-2 border-b border-gray-700">
                      <span className="text-gray-300 capitalize">{category}:</span>
                      <span className="text-white">{item ? `${item.name} - $${item.price}` : "Not selected"}</span>
                    </div>
                  ))}
                </div>

                <div className="border-t border-gray-700 pt-4 mb-6">
                  <div className="flex justify-between items-center text-xl font-bold">
                    <span className="text-white">Total:</span>
                    <span className="text-purple-400">${totalPrice}</span>
                  </div>
                </div>

                <Button className="w-full bg-purple-600 hover:bg-purple-700 text-white" disabled={totalPrice === 0}>
                  Add Custom Outfit to Cart
                </Button>
              </CardContent>
            </Card>
          </div>
        </div>
      </div>
    </div>
  )
}

// Main Homepage Component
export default function HomePage() {
  const [showAdmin, setShowAdmin] = useState(false)
  const [showCustomizer, setShowCustomizer] = useState(false)

  return (
    <div className="min-h-screen bg-black text-white">
      {/* Header */}
      <header className="border-b border-gray-800">
        <div className="container mx-auto px-4 py-4">
          <div className="flex items-center justify-between">
            <div className="flex items-center space-x-4">
              <FloatingLogo size={48} />
              <h1 className="text-2xl font-bold text-white">BIGZSHOPX</h1>
            </div>

            <div className="flex items-center space-x-4">
              <Button
                variant="outline"
                size="sm"
                onClick={() => setShowAdmin(!showAdmin)}
                className={`border-gray-700 text-white hover:bg-gray-800 transition-all ${
                  showAdmin ? "bg-purple-600 border-purple-500" : ""
                }`}
              >
                <Settings className="w-4 h-4 mr-2" />
                Admin {showAdmin && "(Active)"}
              </Button>
              <Button
                variant="outline"
                size="sm"
                className="border-gray-700 text-white hover:bg-gray-800 bg-transparent"
              >
                <ShoppingCart className="w-4 h-4 mr-2" />
                Cart (0)
              </Button>
              <Button
                variant="outline"
                size="sm"
                className="border-gray-700 text-white hover:bg-gray-800 bg-transparent"
              >
                <User className="w-4 h-4" />
              </Button>
            </div>
          </div>
        </div>
      </header>

      <Navigation />

      {/* Admin Panel */}
      {showAdmin && (
        <div className="bg-gradient-to-r from-purple-900/20 to-blue-900/20 border-b border-purple-500/30">
          <div className="container mx-auto px-4 py-2">
            <div className="flex items-center justify-center space-x-2 text-purple-300">
              <Settings className="w-4 h-4" />
              <span className="text-sm font-medium">Admin Mode Active - Manage your inventory below</span>
            </div>
          </div>
        </div>
      )}

      {showAdmin && <AdminPanel />}

      {/* Hero Section */}
      <section className="py-20">
        <div className="container mx-auto px-4 text-center">
          <div className="max-w-4xl mx-auto">
            <div className="flex justify-center mb-8">
              <FloatingLogo size={120} />
            </div>

            <h2 className="text-6xl font-bold mb-6 bg-gradient-to-r from-purple-400 to-purple-600 bg-clip-text text-transparent">
              BIGZSHOPX
            </h2>
            <div className="w-24 h-0.5 bg-purple-500 mx-auto mb-8"></div>
            <p className="text-xl text-gray-300 mb-8 leading-relaxed">
              BIGZSHOPX offers trendy premade outfits and fully customizable clothing that makes you stand out from the
              crowd.
            </p>
            <div className="flex flex-col sm:flex-row gap-4 justify-center">
              <Button
                size="lg"
                className="bg-purple-600 hover:bg-purple-700 text-white px-8 py-3 text-lg font-semibold"
                onClick={() => document.getElementById("products")?.scrollIntoView({ behavior: "smooth" })}
              >
                Shop Now
              </Button>
              <Button
                size="lg"
                variant="outline"
                className="border-purple-500 text-purple-400 hover:bg-purple-500 hover:text-white px-8 py-3 text-lg font-semibold bg-transparent"
                onClick={() => setShowCustomizer(!showCustomizer)}
              >
                Customize Outfit
              </Button>
            </div>
          </div>
        </div>
      </section>

      {/* Custom Outfit Builder */}
      {showCustomizer && <OutfitCustomizer />}

      {/* Product Sections */}
      <div id="products">
        <ProductGrid />
      </div>

      {/* Footer */}
      <footer className="border-t border-gray-800 py-12">
        <div className="container mx-auto px-4">
          <div className="grid grid-cols-1 md:grid-cols-4 gap-8">
            <div>
              <div className="flex items-center space-x-2 mb-4">
                <FloatingLogo size={32} />
                <span className="font-bold">BIGZSHOPX</span>
              </div>
              <p className="text-gray-400">Premium clothing for the modern individual.</p>
            </div>
            <div>
              <h3 className="font-semibold mb-4">Shop</h3>
              <ul className="space-y-2 text-gray-400">
                <li>
                  <a href="#" className="hover:text-white">
                    Men's Collection
                  </a>
                </li>
                <li>
                  <a href="#" className="hover:text-white">
                    Women's Collection
                  </a>
                </li>
                <li>
                  <a href="#" className="hover:text-white">
                    Accessories
                  </a>
                </li>
                <li>
                  <a href="#" className="hover:text-white">
                    Custom Outfits
                  </a>
                </li>
              </ul>
            </div>
            <div>
              <h3 className="font-semibold mb-4">Support</h3>
              <ul className="space-y-2 text-gray-400">
                <li>
                  <a href="#" className="hover:text-white">
                    Contact Us
                  </a>
                </li>
                <li>
                  <a href="#" className="hover:text-white">
                    Size Guide
                  </a>
                </li>
                <li>
                  <a href="#" className="hover:text-white">
                    Returns
                  </a>
                </li>
                <li>
                  <a href="#" className="hover:text-white">
                    FAQ
                  </a>
                </li>
              </ul>
            </div>
            <div>
              <h3 className="font-semibold mb-4">Connect</h3>
              <ul className="space-y-2 text-gray-400">
                <li>
                  <a href="#" className="hover:text-white">
                    Instagram
                  </a>
                </li>
                <li>
                  <a href="#" className="hover:text-white">
                    Twitter
                  </a>
                </li>
                <li>
                  <a href="#" className="hover:text-white">
                    Facebook
                  </a>
                </li>
                <li>
                  <a href="#" className="hover:text-white">
                    TikTok
                  </a>
                </li>
              </ul>
            </div>
          </div>
          <div className="border-t border-gray-800 mt-8 pt-8 text-center text-gray-400">
            <p>&copy; 2025 BIGZSHOPX. All rights reserved.</p>
          </div>
        </div>
      </footer>
    </div>
  )
}
