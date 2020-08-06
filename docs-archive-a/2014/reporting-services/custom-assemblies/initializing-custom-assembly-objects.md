---
title: 사용자 지정 어셈블리 개체 초기화 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- initializing custom assemblies [Reporting Services]
- custom assemblies [Reporting Services], initializing
- OnInit method
ms.assetid: 26fd74dc-d02f-40f7-aeb3-50ce05e9e6b9
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2aba0bd8b71b26651067a2370728dcdff521ceaa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650790"
---
# <a name="initializing-custom-assembly-objects"></a><span data-ttu-id="a07c0-102">사용자 지정 어셈블리 개체 초기화</span><span class="sxs-lookup"><span data-stu-id="a07c0-102">Initializing Custom Assembly Objects</span></span>
  <span data-ttu-id="a07c0-103">사용자 지정 어셈블리 클래스를 인스턴스화할 때 속성 및 필드 값을 초기화해야 하는 경우가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-103">In some cases, you may need to initialize property and field values in your custom assembly classes when you instantiate them.</span></span> <span data-ttu-id="a07c0-104">대개 보고서의 전역 개체 컬렉션에서 제공되는 값으로 사용자 지정 클래스를 초기화해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-104">You will most likely need to initialize your custom classes with values available to you from the report's global object collections.</span></span> <span data-ttu-id="a07c0-105">이 작업은 보고서 **Code** 개체의 **OnInit** 메서드를 다시 정의하여 수행합니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-105">You do this by overriding the **OnInit** method of the **Code** object of a report.</span></span> <span data-ttu-id="a07c0-106">**OnInit**에 액세스하려면 보고서 정의의 **Code** 요소를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-106">To access **OnInit**, use the **Code** element of the report definition.</span></span> <span data-ttu-id="a07c0-107">보고서에서 사용하려는 사용자 지정 어셈블리에 있는 클래스의 속성이나 필드 값을 초기화하는 데는 두 가지 방법이 있습니다. **OnInit**를 사용하여 클래스의 새 인스턴스를 선언 및 만들거나 **OnInit**를 사용하여 공개적으로 사용 가능한 메서드를 호출하는 방법입니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-107">There are two techniques for initializing property or field values of the classes in a custom assembly that you plan to use in your report: You can either declare and create a new instance of your class using **OnInit**, or you can call a publicly available method using **OnInit**.</span></span>  
  
## <a name="global-object-collections-and-initialization"></a><span data-ttu-id="a07c0-108">전역 개체 컬렉션 및 초기화</span><span class="sxs-lookup"><span data-stu-id="a07c0-108">Global Object Collections and Initialization</span></span>  
 <span data-ttu-id="a07c0-109">사용자 지정 클래스 변수를 초기화하는 데 사용할 수 있는 컬렉션이 다수 있으며,</span><span class="sxs-lookup"><span data-stu-id="a07c0-109">Several collections are available to you for initializing your custom class variables.</span></span> <span data-ttu-id="a07c0-110">**Globals** 및 **User** 컬렉션을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-110">You can use the **Globals** and **User** collections.</span></span> <span data-ttu-id="a07c0-111">**Parameters**, **Fields** 및 **ReportItems** 컬렉션은 **OnInit** 메서드가 호출될 때 보고서 수명 주기의 시점에서 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-111">The **Parameters**, **Fields** and **ReportItems** collections are not available to you at the point in the report lifecycle when the **OnInit** method is invoked.</span></span> <span data-ttu-id="a07c0-112">공유 컬렉션인 **Globals** 또는 **User**를 사용하려면 **Report** 개체 참조를 포함시켜야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-112">To use the shared collections, **Globals** or **User**, you need to include the **Report** object reference.</span></span> <span data-ttu-id="a07c0-113">예를 들어, 보고서에 액세스하는 사용자의 현재 언어를 기반으로 사용자 지정 클래스를 초기화하려면 **Code** 요소가 다음과 같을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-113">For example, to initialize your custom class based on the current language of the user accessing the report, your **Code** element might look like the following:</span></span>  
  
```  
<Code>  
   Dim m_myClass As MyClass  
  
   Protected Overrides Sub OnInit()  
      m_myClass = new MyClass(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 <span data-ttu-id="a07c0-114">위에 제시한 대로 클래스의 속성 및 필드 값을 초기화하는 한 가지 방법은 다시 정의된 생성자를 호출하여 클래스를 선언하고 이 클래스의 새 인스턴스를 만드는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-114">One way to initialize the property and field values of a class as shown previously is to declare your class and create a new instance of it by calling an overridden constructor.</span></span>  
  
 <span data-ttu-id="a07c0-115">사용자 지정 어셈블리에서 클래스의 속성 및 필드 값을 초기화하는 또 하나의 방법은 **OnInit** 메서드에서 정의하는 공용으로 사용 가능한 메서드를 호출하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-115">Another way to initialize the property and field values of the classes in your custom assemblies is to call a publicly available method that you define from the **OnInit** method.</span></span> <span data-ttu-id="a07c0-116">먼저 보고서 정의 파일에서 클래스에 대한 인스턴스 이름을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-116">You first need to add an instance name for your class in the report definition file.</span></span> <span data-ttu-id="a07c0-117">올바른 어셈블리 참조 및 인스턴스 이름을 추가하고 나면 초기화 메서드를 호출하여 클래스에 대한 속성 및 필드 값을 초기화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-117">Once you have added the appropriate assembly reference and instance name, you can call your initialization method to initialize property and field values for your class.</span></span> <span data-ttu-id="a07c0-118">**OnInit** 메서드는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="a07c0-118">Your **OnInit** method might look like the following:</span></span>  
  
```  
<Code>  
   Protected Overrides Sub OnInit()  
      m_myClass.MyInitializationMethod(Report.User!Language, _  
         Report.Globals!ExecutionTime)  
   End Sub  
</Code>  
```  
  
 <span data-ttu-id="a07c0-119">사용자 지정 클래스의 어셈블리 참조 및 인스턴스 이름을 추가하는 방법은 [보고서에 어셈블리 참조 추가(&#40;SSRS&#41;)](../report-design/add-an-assembly-reference-to-a-report-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a07c0-119">For more information about adding an assembly reference and instance name for your custom class, see [Add an Assembly Reference to a Report &#40;SSRS&#41;](../report-design/add-an-assembly-reference-to-a-report-ssrs.md).</span></span>  
  
 <span data-ttu-id="a07c0-120">전역 개체 컬렉션에 대한 자세한 내용은 [식의 기본 제공 컬렉션&#40;보고서 작성기 및 SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a07c0-120">For more information about the global object collections, see [Built-in Collections in Expressions &#40;Report Builder and SSRS&#41;](../report-design/built-in-collections-in-expressions-report-builder.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a07c0-121">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a07c0-121">See Also</span></span>  
 [<span data-ttu-id="a07c0-122">보고서에서 사용자 지정 어셈블리 사용</span><span class="sxs-lookup"><span data-stu-id="a07c0-122">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
