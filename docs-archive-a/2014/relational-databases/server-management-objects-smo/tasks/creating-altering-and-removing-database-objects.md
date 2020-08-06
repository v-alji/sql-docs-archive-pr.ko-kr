---
title: 데이터베이스 개체 작업 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- database objects [SMO]
- objects [SMO]
ms.assetid: 702fd63d-8734-4a02-872e-aecfb037c787
author: stevestein
ms.author: sstein
ms.openlocfilehash: 14dd0c0175a23f809fc925c5104ac15ac408805b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739663"
---
# <a name="working-with-database-objects"></a><span data-ttu-id="af5f2-102">데이터베이스 개체 작업</span><span class="sxs-lookup"><span data-stu-id="af5f2-102">Working with Database Objects</span></span>
  <span data-ttu-id="af5f2-103">SMO 개체를 만드는 단계는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-103">The stages of SMO object creation are as follows:</span></span>  
  
1.  <span data-ttu-id="af5f2-104">개체의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-104">Create an instance of the object.</span></span>  
  
2.  <span data-ttu-id="af5f2-105">개체 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-105">Set the object properties.</span></span>  
  
3.  <span data-ttu-id="af5f2-106">자식 개체의 인스턴스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-106">Create instances of the child objects.</span></span>  
  
4.  <span data-ttu-id="af5f2-107">자식 개체 속성을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-107">Set the child object properties.</span></span>  
  
5.  <span data-ttu-id="af5f2-108">개체를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-108">Create the object.</span></span>  
  
 <span data-ttu-id="af5f2-109">SMO 애플리케이션에서 SMO 개체의 인스턴스를 만들 때 이러한 인스턴스는 `Create` 메서드가 실행되기 전까지는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 인스턴스에 존재하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-109">When instances of SMO objects are created in an SMO application, they do not exist on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] until the `Create` method is issued.</span></span> <span data-ttu-id="af5f2-110">그러나 모든 개별 개체에 대해 `Create` 메서드를 실행할 필요는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-110">However, it is not necessary to issue a `Create` method for every individual object.</span></span> <span data-ttu-id="af5f2-111">개체에 자식 개체 집합이 있는 경우 부모 개체만 `Create` 메서드를 실행하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-111">If an object has a set of child objects, only the parent object is required to run the `Create` method.</span></span> <span data-ttu-id="af5f2-112">예를 들어 테이블에 한 개 이상의 열이 있어야 한다는 테이블 정의가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-112">For example, the definition of a table requires that it contains at least one column to exist.</span></span> <span data-ttu-id="af5f2-113">또한 열은 테이블 없이 따로 존재할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-113">Also, a column cannot exist in isolation without a table.</span></span> <span data-ttu-id="af5f2-114">테이블과 테이블의 열은 상호 종속 관계입니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-114">There is a codependent relationship between the table and its columns.</span></span>  
  
 <span data-ttu-id="af5f2-115"><xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> 메서드를 사용하여 개체를 변경할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-115">The <xref:Microsoft.SqlServer.Management.Dmf.Policy.Alter%2A> method lets you make changes to an object.</span></span> <span data-ttu-id="af5f2-116">개체 컬렉션 중 하나에 자식 개체를 추가하거나 속성 값을 변경하는 등의 개체에 대한 여러 변경 작업은 모두 일괄 처리되고 하나의 작업으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-116">Several changes to an object, such as adding child objects to one of the object's collections or changing a property value, are batched together and run as one.</span></span> <span data-ttu-id="af5f2-117">`Alter` 메서드를 사용하면 네트워크 트래픽을 줄이고 전반적인 성능을 개선할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-117">The `Alter` method reduces network traffic and improves overall performance.</span></span>  
  
 <span data-ttu-id="af5f2-118">개체 및 처음 개체를 만들 때 필요했던 모든 상호 종속 자식 개체를 제거하려면 `Drop` 문을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="af5f2-118">The `Drop` statement is used to remove an object and all its codependent child objects that were required to create the object initially.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af5f2-119">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af5f2-119">See Also</span></span>  
 [<span data-ttu-id="af5f2-120">SMO 개체 모델</span><span class="sxs-lookup"><span data-stu-id="af5f2-120">SMO Object Model</span></span>](../smo-object-model.md)  
  
  
