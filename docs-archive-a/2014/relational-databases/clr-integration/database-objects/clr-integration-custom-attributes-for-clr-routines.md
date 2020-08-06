---
title: CLR 루틴에 대 한 사용자 지정 특성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- routines [CLR integration]
- SqlFacet attribute
- SqlTrigger attribute
- SqlProcedure attribute
- custom attributes [CLR integration]
- SqlUserDefinedAggregate attribute
- attributes [CLR integration]
- SqlMethod attribute
- SqlFunction attribute
- common language runtime [SQL Server], attributes
- SqlUserDefinedTypeAttribute attribute
ms.assetid: 95069d22-b05d-4670-b053-15ee2a664e33
author: rothja
ms.author: jroth
ms.openlocfilehash: 058bbec7f0f1f63fbd96258a0abe7a6c3d543d88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638845"
---
# <a name="custom-attributes-for-clr-routines"></a><span data-ttu-id="e7185-102">CLR 루틴용 사용자 지정 특성</span><span class="sxs-lookup"><span data-stu-id="e7185-102">Custom Attributes for CLR Routines</span></span>
  <span data-ttu-id="e7185-103">에 등록 된 CLR (공용 언어 런타임) 루틴, 사용자 정의 형식 및 사용자 정의 집계에 나열 된 특성을 적용할 수 있습니다 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="e7185-103">The attributes listed can be applied to common language runtime (CLR) routines, user-defined types, and user-defined aggregates that are registered in [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="e7185-104">특성이 적용되지 않으면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]는 기본값을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="e7185-104">If the attribute is not applied, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assumes the default value.</span></span> <span data-ttu-id="e7185-105">나열된 특성은 `Microsoft.SqlServer.Server` 네임스페이스에 정의됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7185-105">The attributes listed are defined in the `Microsoft.SqlServer.Server` namespace.</span></span>  
  
## <a name="the-sqluserdefinedaggregate-attribute"></a><span data-ttu-id="e7185-106">SqlUserDefinedAggregate 특성</span><span class="sxs-lookup"><span data-stu-id="e7185-106">The SqlUserDefinedAggregate Attribute</span></span>  
 <span data-ttu-id="e7185-107">`SqlUserDefinedAggregate` 특성은 메서드를 사용자 정의 집계로 등록해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e7185-107">The `SqlUserDefinedAggregate` attribute indicates that the method should be registered as a user-defined aggregate.</span></span> <span data-ttu-id="e7185-108">모든 사용자 정의 집계에는 이 특성이 주석으로 첨부되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="e7185-108">Every user-defined aggregate must be annotated with this attribute.</span></span>  
  
 <span data-ttu-id="e7185-109">자세한 내용은 [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7185-109">For more information, see [SqlUserDefinedAggregateAttribute](https://go.microsoft.com/fwlink/?LinkId=124626).</span></span>  
  
## <a name="the-sqlfunction-attribute"></a><span data-ttu-id="e7185-110">SqlFunction 특성</span><span class="sxs-lookup"><span data-stu-id="e7185-110">The SqlFunction Attribute</span></span>  
 <span data-ttu-id="e7185-111">`SqlFunction` 특성은 적절한 함수 특성 집합을 사용하여 메서드를 함수로 등록해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e7185-111">The `SqlFunction` attribute indicates the method should be registered as a function, with the appropriate function attributes set.</span></span>  
  
 <span data-ttu-id="e7185-112">자세한 내용은 [SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7185-112">For more information, see [SqlFunctionAttribute](https://go.microsoft.com/fwlink/?LinkId=128019).</span></span>  
  
## <a name="the-sqlfacet-attribute"></a><span data-ttu-id="e7185-113">SqlFacet 특성</span><span class="sxs-lookup"><span data-stu-id="e7185-113">The SqlFacet Attribute</span></span>  
 <span data-ttu-id="e7185-114">`SqlFacet` 특성은 UDT(사용자 정의 형식) 식의 반환 형식에 대한 정보를 반환하는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7185-114">The `SqlFacet` attribute is used to return information about the return type of a user-defined type (UDT) expression.</span></span>  
  
 <span data-ttu-id="e7185-115">자세한 내용은 [SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7185-115">For more information, see [SqlFacetAttribute](https://go.microsoft.com/fwlink/?LinkId=128020).</span></span>  
  
## <a name="the-sqlprocedure-attribute"></a><span data-ttu-id="e7185-116">SqlProcedure 특성</span><span class="sxs-lookup"><span data-stu-id="e7185-116">The SqlProcedure Attribute</span></span>  
 <span data-ttu-id="e7185-117">`SqlProcedure` 특성은 메서드를 저장 프로시저로 등록해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e7185-117">The `SqlProcedure` attribute indicates the method should be registered as a stored procedure.</span></span> <span data-ttu-id="e7185-118">이 특성은 Visual Studio에서 지정한 메서드를 저장 프로시저로 자동으로 등록하는 데만 사용되며 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서는 사용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="e7185-118">This attribute is used only by Visual Studio to register the specified method as a stored procedure automatically; it is not used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="e7185-119">자세한 내용은 [SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7185-119">For more information, see [SqlProcedureAttribute](https://go.microsoft.com/fwlink/?LinkId=128021).</span></span>  
  
## <a name="the-sqltrigger-attribute"></a><span data-ttu-id="e7185-120">SqlTrigger 특성</span><span class="sxs-lookup"><span data-stu-id="e7185-120">The SqlTrigger Attribute</span></span>  
 <span data-ttu-id="e7185-121">`SqlTrigger` 특성은 메서드를 트리거로 등록해야 함을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="e7185-121">The `SqlTrigger` attribute indicates the method should be registered as a trigger.</span></span>  
  
 <span data-ttu-id="e7185-122">자세한 내용은 [Sqltriggercontext](https://go.microsoft.com/fwlink/?LinkId=128022) 및 [sqltriggercontext](https://go.microsoft.com/fwlink/?LinkId=203898)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="e7185-122">For more information, see [SqlTriggerContext](https://go.microsoft.com/fwlink/?LinkId=128022) and [SqlTriggerAttribute](https://go.microsoft.com/fwlink/?LinkId=203898).</span></span>  
  
## <a name="the-sqluserdefinedtypeattribute"></a><span data-ttu-id="e7185-123">SqlUserDefinedTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="e7185-123">The SqlUserDefinedTypeAttribute</span></span>  
 <span data-ttu-id="e7185-124">어셈블리의 클래스 정의에 SqlUserDefinedTypeAttribute를 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="e7185-124">You can apply the SqlUserDefinedTypeAttribute to a class definition in the assembly.</span></span> <span data-ttu-id="e7185-125">이렇게 하면 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]에서 이 사용자 지정 특성을 가진 클래스 정의에 바인딩되는 사용자 정의 형식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="e7185-125">It causes [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to create a user-defined type that is bound to the class definition which has this custom attribute.</span></span>  
  
 <span data-ttu-id="e7185-126">자세한 내용은 [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7185-126">For more information, see [SqlUserDefinedTypeAttribute](https://go.microsoft.com/fwlink/?LinkId=128024).</span></span>  
  
## <a name="the-sqlmethod-attribute"></a><span data-ttu-id="e7185-127">SqlMethod 특성</span><span class="sxs-lookup"><span data-stu-id="e7185-127">The SqlMethod Attribute</span></span>  
 <span data-ttu-id="e7185-128">`SqlMethod` 특성은 UDT의 속성 또는 메서드의 결정성 및 데이터 액세스 속성을 나타내는 데 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="e7185-128">The `SqlMethod` attribute is used to indicate the determinism and data access properties of a method or a property on a UDT.</span></span>  
  
 <span data-ttu-id="e7185-129">자세한 내용은 [SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="e7185-129">For more information, see [SqlMethodAttribute](https://go.microsoft.com/fwlink/?LinkId=128025).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7185-130">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e7185-130">See Also</span></span>  
 <span data-ttu-id="e7185-131">[CLR 사용자 정의 집계](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md) </span><span class="sxs-lookup"><span data-stu-id="e7185-131">[CLR User-Defined Aggregates](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-aggregates.md) </span></span>  
 <span data-ttu-id="e7185-132">[CLR 사용자 정의 함수](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span><span class="sxs-lookup"><span data-stu-id="e7185-132">[CLR User-Defined Functions](../../clr-integration-database-objects-user-defined-functions/clr-user-defined-functions.md) </span></span>  
 <span data-ttu-id="e7185-133">[CLR 사용자 정의 형식](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span><span class="sxs-lookup"><span data-stu-id="e7185-133">[CLR User-Defined Types](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md) </span></span>  
 <span data-ttu-id="e7185-134">[CLR 저장 프로시저](../../../database-engine/dev-guide/clr-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="e7185-134">[CLR Stored Procedures](../../../database-engine/dev-guide/clr-stored-procedures.md) </span></span>  
 [<span data-ttu-id="e7185-135">CLR 트리거</span><span class="sxs-lookup"><span data-stu-id="e7185-135">CLR Triggers</span></span>](../../../database-engine/dev-guide/clr-triggers.md)  
  
  
