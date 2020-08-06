---
title: 식을 통해 사용자 지정 어셈블리 액세스 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- expressions [Reporting Services], custom assemblies
- static member calls
- instance member calls [Reporting Services]
- calling class members
- custom assemblies [Reporting Services], expressions
ms.assetid: 917c4d47-1a95-4f54-98b1-e8cb2165d90f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 99497de0456d90fd522ce27c62fd5aa1b812059f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638551"
---
# <a name="accessing-custom-assemblies-through-expressions"></a><span data-ttu-id="2f15c-102">식을 통해 사용자 지정 어셈블리 액세스</span><span class="sxs-lookup"><span data-stu-id="2f15c-102">Accessing Custom Assemblies Through Expressions</span></span>
  <span data-ttu-id="2f15c-103">사용자 지정 어셈블리를 만들어 보고서 디자이너 또는 보고서 서버에서 사용할 수 있도록 했으며, 적절한 보안 정책을 추가하고, 보고서 정의에서 사용자 지정 어셈블리에 대한 참조를 추가했으면 보고서 식을 사용하여 어셈블리의 클래스 멤버에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-103">Once you have created a custom assembly, made it available to Report Designer or the report server, added the appropriate security policy, and added a reference to your custom assembly in your report definition, you can access the members of the classes in your assembly using report expressions.</span></span> <span data-ttu-id="2f15c-104">식의 사용자 지정 코드를 참조하려면 어셈블리 내에서 클래스의 멤버를 호출해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-104">To refer to custom code in an expression, you must call the member of a class within the assembly.</span></span> <span data-ttu-id="2f15c-105">이 방법은 메서드가 정적인지 아니면 인스턴스 기반인지에 따라 달라집니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-105">How you do this depends on whether the method is static or instance-based.</span></span>  
  
## <a name="calling-static-members-from-a-report-definition-file"></a><span data-ttu-id="2f15c-106">보고서 정의 파일에서 정적 멤버 호출</span><span class="sxs-lookup"><span data-stu-id="2f15c-106">Calling Static Members from a Report Definition File</span></span>  
 <span data-ttu-id="2f15c-107">정적 멤버는 인스턴스화된 개체가 아닌 클래스 또는 형식 자체에 속합니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-107">Static members belong to the class or type itself and not to an instantiated object.</span></span> <span data-ttu-id="2f15c-108">이러한 멤버는 클래스에서 직접 호출하여 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-108">These members can be accessed by directly calling them from the class.</span></span> <span data-ttu-id="2f15c-109">정적 멤버가 기능을 가장 잘 수행하므로 보고서에서 사용자 지정 함수를 호출하려면 가능하면 항상 정적 멤버를 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-109">You should use static members to call custom functions in a report whenever possible, because static members perform best.</span></span> <span data-ttu-id="2f15c-110">정적 멤버를 호출하려면 =*Namespace.Class.Method* 형식의 식으로 정적 멤버를 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-110">To call a static member, you need to reference it as an expression that takes the form =*Namespace.Class.Method*.</span></span>  
  
#### <a name="to-call-static-members"></a><span data-ttu-id="2f15c-111">정적 멤버를 호출하려면</span><span class="sxs-lookup"><span data-stu-id="2f15c-111">To call static members</span></span>  
  
-   <span data-ttu-id="2f15c-112">정적 멤버를 호출하려면 네임스페이스, 클래스 이름 및 멤버 이름이 포함된 멤버의 정규화된 이름과 동일하게 식을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-112">To call a static member, set your expression equal to the fully qualified name of the member, which includes the namespace, class name, and member name.</span></span> <span data-ttu-id="2f15c-113">다음 예는 **StandardCost** 필드 값을 달러에서 파운드로 변환하고 이를 보고서에 표시하는 **ToGBP** 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-113">The following example calls the **ToGBP** method, which converts the **StandardCost** field value from dollars to pounds sterling and displays it in a report:</span></span>  
  
    ```  
    =CurrencyConversion.DollarCurrencyConversion.ToGBP(Fields!StandardCost.Value)  
    ```  
  
### <a name="important-information-regarding-static-fields-and-properties"></a><span data-ttu-id="2f15c-114">정적 필드 및 속성 관련 중요 정보</span><span class="sxs-lookup"><span data-stu-id="2f15c-114">Important Information Regarding Static Fields and Properties</span></span>  
 <span data-ttu-id="2f15c-115">현재 모든 보고서는 동일한 애플리케이션 도메인에서 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-115">Currently, all reports are executed in the same application domain.</span></span> <span data-ttu-id="2f15c-116">이것은 사용자별 정적 데이터가 있는 보고서에서 동일한 보고서의 다른 인스턴스에 이 데이터를 공개한다는 의미입니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-116">This means that reports with user-specific, static data expose this data to other instances of the same report.</span></span> <span data-ttu-id="2f15c-117">이에 따라 특정 보고서를 현재 실행하고 있는 모든 사용자가 한 사용자의 정적 데이터를 사용할 수 있게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-117">This condition might make it possible for the static data of one user to be available to all users currently running a particular report.</span></span> <span data-ttu-id="2f15c-118">그러므로 사용자 지정 어셈블리 또는 **Code** 요소의 정적 필드나 속성을 사용하지 말고 그 대신 보고서의 인스턴스 필드나 속성을 사용하는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-118">For this reason, it is highly recommended that you not use static fields or properties in custom assemblies or in the **Code** element; instead, use instance fields or properties in your reports.</span></span> <span data-ttu-id="2f15c-119">정적 메서드는 상태나 데이터를 저장하지 않으므로 계속 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-119">Static methods can still be used, because they do not store state or data.</span></span>  
  
## <a name="calling-instance-members-from-a-report-definition-file"></a><span data-ttu-id="2f15c-120">보고서 정의 파일에서 인스턴스 멤버 호출</span><span class="sxs-lookup"><span data-stu-id="2f15c-120">Calling Instance Members from a Report Definition File</span></span>  
 <span data-ttu-id="2f15c-121">액세스해야 할 보고서 정의 내 인스턴스 멤버가 사용자 지정 어셈블리에 포함되어 있는 경우 클래스에 대한 인스턴스 이름을 보고서에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-121">If your custom assembly contains instance members that you need to access in a report definition, you must add an instance name for your class to the report.</span></span> <span data-ttu-id="2f15c-122">**보고서 속성** 대화 상자의 **코드** 탭을 사용하여 클래스에 대한 인스턴스 이름을 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-122">You can add an instance name for a class using the **Code** tab of the **Report Properties** dialog.</span></span> <span data-ttu-id="2f15c-123">보고서에 클래스의 인스턴스를 추가하는 데 대한 자세한 내용은 [보고서 디자이너의 식에 포함된 사용자 지정 코드 및 어셈블리 참조&#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="2f15c-123">For more information about adding instances of classes to a report, see [Custom Code and Assembly References in Expressions in Report Designer &#40;SSRS&#41;](../report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md).</span></span>  
  
 <span data-ttu-id="2f15c-124">정적 멤버를 호출 하려면 = Code 형식의 식으로 정적 멤버를 참조 해야*합니다. InstanceName. 메서드*.</span><span class="sxs-lookup"><span data-stu-id="2f15c-124">To call a static member, you need to reference it as an expression that takes the form = Code *.InstanceName.Method*.</span></span>  
  
#### <a name="to-call-instance-members"></a><span data-ttu-id="2f15c-125">인스턴스 멤버를 호출하려면</span><span class="sxs-lookup"><span data-stu-id="2f15c-125">To call instance members</span></span>  
  
-   <span data-ttu-id="2f15c-126">사용자 지정 어셈블리의 인스턴스 멤버를 호출하려면 인스턴스 이름 및 메서드가 뒤에 나오는 **Code** 키워드를 참조해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-126">To call an instance member of a custom assembly, you must reference the **Code** keyword followed by the instance name and the method.</span></span> <span data-ttu-id="2f15c-127">다음 예에서는 **StandardCost** 필드 값을 달러에서 유로로 변환하고 이를 보고서에 표시하는 인스턴스 메서드 **ToEUR**을 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="2f15c-127">The following example calls an instance method **ToEUR** which converts the **StandardCost** field value from dollars to euros and displays it in a report:</span></span>  
  
    ```  
    =Code.m_myDollarCoversion.ToEUR(Fields!StandardCost.Value)  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="2f15c-128">참고 항목</span><span class="sxs-lookup"><span data-stu-id="2f15c-128">See Also</span></span>  
 [<span data-ttu-id="2f15c-129">보고서에서 사용자 지정 어셈블리 사용</span><span class="sxs-lookup"><span data-stu-id="2f15c-129">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
