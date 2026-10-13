---
layout: ph-tree
transition: none
noteType: warning
meta: "app/Actions/"
---

# O ecommerce que eu herdei

::tree::

```text {2}
app/
├── Actions/           ← 👈
├── Console/
├── Data/
├── Enums/
├── Events/
├── Exceptions/
├── Http/
├── Jobs/
├── Listeners/
├── Livewire/
├── Mail/
├── Models/
├── Notifications/
├── Observers/
├── Policies/
├── Providers/
├── Services/
└── Support/
```

::content::

### `app/Actions/` — 15 arquivos

```text {all}{class:'!text-xs'}
├── ApplyCouponAction.php
├── CalculateShippingAction.php
├── CalculateTaxAction.php
├── CancelOrderAction.php
├── CreateCustomerAction.php
├── CreateOrderAction.php
├── CreateProductAction.php
├── CreateRefundAction.php
├── ProcessCheckoutAction.php
├── ProcessPaymentAction.php
├── ProcessRefundAction.php
├── SyncInventoryAction.php
├── UpdateOrderStatusAction.php
├── UpdateProductAction.php
└── ValidateStockAction.php
```

::note::

**5 domínios diferentes** numa pasta só: produto, pedido, cupom, frete e estoque — agrupados porque são "Actions".

<!-- "Actions: criar produto, aplicar cupom, calcular frete, cancelar pedido — tudo misturado." -->

<!-- ============================================ -->
<!-- STEPPER: app/Data/ (line 4)                  -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: info
meta: "app/Data/"
---

# O ecommerce que eu herdei

::tree::

```text {4}
app/
├── Actions/
├── Console/
├── Data/              ← 👈
├── Enums/
├── Events/
├── Exceptions/
├── Http/
├── Jobs/
├── Listeners/
├── Livewire/
├── Mail/
├── Models/
├── Notifications/
├── Observers/
├── Policies/
├── Providers/
├── Services/
└── Support/
```

::content::

### `app/Data/` — 10 DTOs

```text {all}{class:'!text-xs'}
├── AddressData.php
├── CartData.php
├── CheckoutData.php
├── CustomerData.php
├── OrderData.php
├── PaymentData.php
├── ProductData.php
├── ShipmentData.php
├── ShippingRateData.php
└── TaxCalculationData.php
```

::note::

`CheckoutData` e `ShipmentData` representam **fluxos completamente distintos** mas moram na mesma pasta porque são "Data".

<!-- "Data: DTOs. CheckoutData, PaymentData e ProductData na mesma pasta. Cada um pertence a um fluxo diferente." -->

<!-- ============================================ -->
<!-- STEPPER: app/Enums/ (line 5)                 -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: danger
meta: "app/Enums/"
---

# O ecommerce que eu herdei

::tree::

```text {5}
app/
├── Actions/
├── Console/
├── Data/
├── Enums/             ← 👈
├── Events/
├── Exceptions/
├── Http/
├── Jobs/
├── Listeners/
├── Livewire/
├── Mail/
├── Models/
├── Notifications/
├── Observers/
├── Policies/
├── Providers/
├── Services/
└── Support/
```

::content::

### `app/Enums/` — 8 arquivos

```text {all}{class:'!text-xs'}
├── CarrierType.php
├── CouponType.php
├── DiscountType.php
├── OrderStatus.php
├── PaymentMethod.php
├── PaymentStatus.php
├── ProductStatus.php
└── ShipmentStatus.php
```

::note::

`OrderStatus`, `PaymentStatus` e `ShipmentStatus` — **3 domínios** com ciclos de vida independentes na mesma pasta.

<!-- "Enums: OrderStatus, PaymentStatus e ShipmentStatus moram juntos. Três domínios completamente diferentes." -->

<!-- ============================================ -->
<!-- STEPPER: app/Events/ (line 6)                -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: warning
meta: "app/Events/"
---

# O ecommerce que eu herdei

::tree::

```text {6}
app/
├── Actions/
├── Console/
├── Data/
├── Enums/
├── Events/            ← 👈
├── Exceptions/
├── Http/
├── Jobs/
├── Listeners/
├── Livewire/
├── Mail/
├── Models/
├── Notifications/
├── Observers/
├── Policies/
├── Providers/
├── Services/
└── Support/
```

::content::

### `app/Events/` — 12 arquivos

```text {all}{class:'!text-xs'}
├── CartAbandoned.php
├── CouponApplied.php
├── CustomerRegistered.php
├── InventoryLow.php
├── OrderCancelled.php
├── OrderPlaced.php
├── OrderStatusUpdated.php
├── PaymentConfirmed.php
├── PaymentFailed.php
├── ProductCreated.php
├── RefundProcessed.php
└── ShipmentCreated.php
```

::note::

`OrderPlaced`, `PaymentConfirmed` e `ShipmentCreated` representam **3 etapas de módulos diferentes** — mas moram juntos.

<!-- "Events: 3 domínios completamente diferentes na mesma pasta." -->

<!-- ============================================ -->
<!-- STEPPER: app/Http/ (line 8)                  -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: warning
meta: "app/Http/"
---

# O ecommerce que eu herdei

::tree::

```text {8}
app/
├── Actions/
├── Console/
├── Data/
├── Enums/
├── Events/
├── Exceptions/
├── Http/              ← 👈
├── Jobs/
├── Listeners/
├── Livewire/
├── Mail/
├── Models/
├── Notifications/
├── Observers/
├── Policies/
├── Providers/
├── Services/
└── Support/
```

::content::

### `app/Http/` — 25 arquivos

```text {all}{class:'!text-xs'}
├── Controllers/
│   ├── CartController.php
│   ├── CategoryController.php
│   ├── CheckoutController.php
│   ├── CouponController.php
│   ├── CustomerController.php
│   ├── DashboardController.php
│   ├── DiscountController.php
│   ├── InventoryController.php
│   ├── OrderController.php
│   ├── PaymentWebhookController.php
│   ├── ProductController.php
│   ├── RefundController.php
│   ├── ReportController.php
│   ├── ReviewController.php
│   ├── SearchController.php
│   ├── ShippingController.php
│   ├── SupplierController.php
│   └── WebhookController.php
├── Middleware/
│   ├── CheckOrderOwnership.php
│   ├── ValidateCartNotEmpty.php
│   └── VerifyWebhookSignature.php
└── Requests/
    ├── CreateOrderRequest.php
    ├── CreateProductRequest.php
    ├── ProcessCheckoutRequest.php
    └── UpdateCartRequest.php
```

::note::

**18 controllers** de domínios distintos lado a lado. Middleware e Requests misturados junto.

<!-- "Http: controllers de produto, carrinho, checkout, pagamento, frete — tudo junto." -->

<!-- ============================================ -->
<!-- STEPPER: app/Jobs/ (line 9)                  -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: danger
meta: "app/Jobs/"
---

# O ecommerce que eu herdei

::tree::

```text {9}
app/
├── Actions/
├── Console/
├── Data/
├── Enums/
├── Events/
├── Exceptions/
├── Http/
├── Jobs/              ← 👈
├── Listeners/
├── Livewire/
├── Mail/
├── Models/
├── Notifications/
├── Observers/
├── Policies/
├── Providers/
├── Services/
└── Support/
```

::content::

### `app/Jobs/` — 18 arquivos

```text {all}{class:'!text-xs'}
├── CalculateShippingJob.php
├── ChargePaymentJob.php
├── CleanupExpiredCartsJob.php
├── ConfirmPaymentJob.php
├── ExportOrdersJob.php
├── GenerateInvoiceJob.php
├── ImportProductsJob.php
├── NotifyLowStockJob.php
├── ProcessOrderJob.php
├── ProcessRefundJob.php
├── ProcessWebhookJob.php
├── RecalculatePricingJob.php
├── SendAbandonedCartEmailJob.php
├── SendOrderConfirmationJob.php
├── SendShipmentTrackingJob.php
├── SendTrackingEmailJob.php
├── SyncInventoryJob.php
└── UpdateExchangeRatesJob.php
```

::note::

`ChargePaymentJob` e `ImportProductsJob` rodam na **mesma fila** por padrão. Zero relação entre eles.

<!-- "Jobs: ChargePaymentJob cobra o cliente. ImportProductsJob importa planilha. Zero relação." -->

<!-- ============================================ -->
<!-- STEPPER: app/Listeners/ (line 10)            -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: danger
meta: "app/Listeners/"
---

# O ecommerce que eu herdei

::tree::

```text {10}
app/
├── Actions/
├── Console/
├── Data/
├── Enums/
├── Events/
├── Exceptions/
├── Http/
├── Jobs/
├── Listeners/         ← 👈
├── Livewire/
├── Mail/
├── Models/
├── Notifications/
├── Observers/
├── Policies/
├── Providers/
├── Services/
└── Support/
```

::content::

### `app/Listeners/` — 10 arquivos

```text {all}{class:'!text-xs'}
├── CreateShipmentOnPayment.php
├── DeductInventory.php
├── LogOrderStatusChange.php
├── NotifyCustomerOrderPlaced.php
├── NotifyWarehouse.php
├── ProcessPaymentOnOrder.php
├── RecalculateCartTotal.php
├── SendRefundConfirmation.php
├── SendWelcomeEmail.php
└── UpdateInventory.php
```

::note::

**Quem escuta quem?** Impossível saber sem abrir cada arquivo. O acoplamento está invisível.

<!-- "Listeners: ProcessPaymentOnOrder e CreateShipmentOnPayment moram juntos. Pra saber quem escuta quem, precisa abrir cada arquivo." -->

<!-- ============================================ -->
<!-- STEPPER: app/Livewire/ (line 11)             -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: info
meta: "app/Livewire/"
---

# O ecommerce que eu herdei

::tree::

```text {11}
app/
├── Actions/
├── Console/
├── Data/
├── Enums/
├── Events/
├── Exceptions/
├── Http/
├── Jobs/
├── Listeners/
├── Livewire/          ← 👈
├── Mail/
├── Models/
├── Notifications/
├── Observers/
├── Policies/
├── Providers/
├── Services/
└── Support/
```

::content::

### `app/Livewire/` — 8 componentes

```text {all}{class:'!text-xs'}
├── CartSummary.php
├── CheckoutForm.php
├── CustomerDashboard.php
├── OrderHistory.php
├── ProductCatalog.php
├── ProductFilter.php
├── ReviewForm.php
└── WishlistPage.php
```

::note::

Catálogo, checkout e wishlist — **3 experiências de usuário** completamente diferentes no mesmo lugar.

<!-- "Livewire: ProductCatalog e CheckoutForm são vizinhos. Um exibe produtos, o outro finaliza compra." -->

<!-- ============================================ -->
<!-- STEPPER: app/Mail/ (line 12)                 -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: info
meta: "app/Mail/"
---

# O ecommerce que eu herdei

::tree::

```text {12}
app/
├── Actions/
├── Console/
├── Data/
├── Enums/
├── Events/
├── Exceptions/
├── Http/
├── Jobs/
├── Listeners/
├── Livewire/
├── Mail/              ← 👈
├── Models/
├── Notifications/
├── Observers/
├── Policies/
├── Providers/
├── Services/
└── Support/
```

::content::

### `app/Mail/` — 6 arquivos

```text {all}{class:'!text-xs'}
├── AbandonedCartMail.php
├── InvoiceMail.php
├── OrderConfirmationMail.php
├── RefundConfirmationMail.php
├── ShipmentTrackingMail.php
└── WelcomeMail.php
```

::note::

`OrderConfirmationMail` é **pós-venda**. `AbandonedCartMail` é **marketing**. Vizinhos de pasta, domínios opostos.

<!-- "Mail: email de confirmação de pedido e de carrinho abandonado. Domínios opostos." -->

<!-- ============================================ -->
<!-- STEPPER: app/Models/ (line 13)               -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: danger
meta: "app/Models/"
---

# O ecommerce que eu herdei

::tree::

```text {13}
app/
├── Actions/
├── Console/
├── Data/
├── Enums/
├── Events/
├── Exceptions/
├── Http/
├── Jobs/
├── Listeners/
├── Livewire/
├── Mail/
├── Models/           ← 👈
├── Notifications/
├── Observers/
├── Policies/
├── Providers/
├── Services/
└── Support/
```

::content::

### `app/Models/` — 45 arquivos

```text {all}{class:'!text-xs'}
├── Brand.php
├── Carrier.php
├── Cart.php
├── CartItem.php
├── Category.php
├── Coupon.php
├── Customer.php
├── Discount.php
├── Inventory.php
├── InventoryHistory.php
├── Order.php
├── OrderItem.php
├── Payment.php
├── PaymentMethod.php
├── PaymentTransaction.php
├── Product.php
├── ProductAttribute.php
├── ProductVariant.php
├── Refund.php
├── Review.php
├── Shipment.php
├── ShipmentItem.php
├── ShippingMethod.php
├── ShippingRate.php
├── ShippingZone.php
├── Tax.php
├── User.php
├── Warehouse.php
├── Wishlist.php
└── … +16 arquivos
```

::note::

**45 models.** `Product` e `PaymentTransaction` são vizinhos. `Cart` e `Warehouse` no mesmo diretório. Nada em comum.

<!-- "Models: 45 arquivos. Product, PaymentTransaction, Carrier, Coupon — todos vizinhos. Nada em comum." -->

<!-- ============================================ -->
<!-- STEPPER: app/Notifications/ (line 14)        -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: warning
meta: "app/Notifications/"
---

# O ecommerce que eu herdei

::tree::

```text {14}
app/
├── Actions/
├── Console/
├── Data/
├── Enums/
├── Events/
├── Exceptions/
├── Http/
├── Jobs/
├── Listeners/
├── Livewire/
├── Mail/
├── Models/
├── Notifications/     ← 👈
├── Observers/
├── Policies/
├── Providers/
├── Services/
└── Support/
```

::content::

### `app/Notifications/` — 6 arquivos

```text {all}{class:'!text-xs'}
├── LowStockNotification.php
├── NewOrderNotification.php
├── OrderStatusNotification.php
├── PaymentFailedNotification.php
├── RefundNotification.php
└── ShipmentNotification.php
```

::note::

`LowStockNotification` é **operação interna**. `PaymentFailedNotification` é **financeiro**. Domínios opostos, mesma pasta.

<!-- "Notifications: LowStockNotification é de estoque, PaymentFailedNotification é de pagamento. Opostos, mas vizinhos." -->

<!-- ============================================ -->
<!-- STEPPER: app/Observers/ (line 15)            -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: info
meta: "app/Observers/"
---

# O ecommerce que eu herdei

::tree::

```text {15}
app/
├── Actions/
├── Console/
├── Data/
├── Enums/
├── Events/
├── Exceptions/
├── Http/
├── Jobs/
├── Listeners/
├── Livewire/
├── Mail/
├── Models/
├── Notifications/
├── Observers/         ← 👈
├── Policies/
├── Providers/
├── Services/
└── Support/
```

::content::

### `app/Observers/` — 5 arquivos

```text {all}{class:'!text-xs'}
├── CartObserver.php
├── InventoryObserver.php
├── OrderObserver.php
├── PaymentObserver.php
└── ProductObserver.php
```

::note::

Side effects de **5 domínios** escondidos em hooks mágicos. Difícil rastrear o que dispara o quê.

<!-- "Observers: OrderObserver observa pedidos, InventoryObserver observa estoque. Responsabilidades diferentes." -->

<!-- ============================================ -->
<!-- STEPPER: app/Services/ (line 18)             -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: danger
meta: "app/Services/"
---

# O ecommerce que eu herdei

::tree::

```text {18}
app/
├── Actions/
├── Console/
├── Data/
├── Enums/
├── Events/
├── Exceptions/
├── Http/
├── Jobs/
├── Listeners/
├── Livewire/
├── Mail/
├── Models/
├── Notifications/
├── Observers/
├── Policies/
├── Providers/
├── Services/           ← 👈
└── Support/
```

::content::

### `app/Services/` — 22 arquivos

```text {all}{class:'!text-xs'}
├── CartService.php
├── CatalogService.php
├── CheckoutService.php
├── CouponService.php
├── CurrencyService.php
├── CustomerService.php
├── DiscountService.php
├── FraudDetectionService.php
├── InventoryService.php
├── NotificationService.php
├── OrderService.php
├── PaymentGatewayService.php
├── PricingService.php
├── ProductImportService.php
├── ProductService.php
├── RefundService.php
├── ReportService.php
├── SearchService.php
├── ShippingService.php
├── StockService.php
├── TaxService.php
└── WishlistService.php
```

::note::

**22 "Services"** — `ProductService` e `ShippingService` não compartilham nenhum import, nenhuma interface, nenhum conceito.

<!-- "Services: 22 arquivos. ProductService e ShippingService são estranhos morando na mesma casa." -->

<!-- ============================================ -->
<!-- STEPPER: O resto (Console, Exceptions,       -->
<!--   Policies, Providers, Support)              -->
<!-- ============================================ -->
---
layout: ph-tree
transition: none
noteType: info
meta: "o resto"
---

# O ecommerce que eu herdei

::tree::

```text {3,7,16,17,19}
app/
├── Actions/
├── Console/           ← 👈
├── Data/
├── Enums/
├── Events/
├── Exceptions/        ← 👈
├── Http/
├── Jobs/
├── Listeners/
├── Livewire/
├── Mail/
├── Models/
├── Notifications/
├── Observers/
├── Policies/          ← 👈
├── Providers/         ← 👈
├── Services/
├── Support/           ← 👈
```

::content::

### O resto — 20 arquivos

```text {all}{class:'!text-xs ph-dense'}
app/Console/
├── CleanupCartsCommand.php
├── RecalculateStockCommand.php
└── SyncCurrenciesCommand.php

app/Exceptions/
├── InsufficientStockException.php
├── InvalidCouponException.php
├── PaymentDeclinedException.php
└── ShippingUnavailableException.php

app/Policies/
├── CustomerPolicy.php
├── OrderPolicy.php
├── ProductPolicy.php
└── ReviewPolicy.php

app/Providers/
├── AppServiceProvider.php
├── AuthServiceProvider.php
├── EventServiceProvider.php
└── RouteServiceProvider.php

app/Support/
├── CartCalculator.php
├── CurrencyFormatter.php
├── MoneyHelper.php
├── PriceFormatter.php
└── SlugGenerator.php
```

::note::

Até as exceptions misturadas: `InsufficientStockException` e `PaymentDeclinedException` — estoque e pagamento lado a lado.

<!-- "O resto: Console, Exceptions, Policies, Providers, Support. Tudo separado por tipo técnico." -->

