---
title: Diffgram를 사용 하 여 SQLXML 4.0에서 데이터 수정 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- data deletions [SQLXML]
- updating data [SQLXML]
- DiffGrams [SQLXML]
- modifying data [SQLXML]
- .NET Framework [SQLXML], DiffGrams
- XML [SQLXML]
- database modifications [SQLXML]
- data updates [SQLXML]
- data modifications [SQLXML]
- record insertion [SQLXML]
- SQLXML, DiffGrams
- deleting data
- record updates [SQLXML]
- record deletions [SQLXML]
ms.assetid: 48b8a8f9-f3af-404f-8c84-f4c3703364d9
author: rothja
ms.author: jroth
ms.openlocfilehash: cc2e24304679a7648f18148eb45f33b9bf719a9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651584"
---
# <a name="using-diffgrams-to-modify-data-in-sqlxml-40"></a><span data-ttu-id="3fb7e-102">SQLXML 4.0에서 DiffGram을 사용하여 데이터 수정</span><span class="sxs-lookup"><span data-stu-id="3fb7e-102">Using DiffGrams to Modify Data in SQLXML 4.0</span></span>
  <span data-ttu-id="3fb7e-103">DiffGram 형식은 .NET Framework의 **데이터 집합** 구성 요소에 도입 됩니다 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="3fb7e-103">The DiffGram format is introduced in the **DataSet** component of the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework.</span></span> <span data-ttu-id="3fb7e-104">.NET Framework 내에서 DiffGram을 만들고 사용하여 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 데이터베이스의 테이블에 있는 데이터를 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="3fb7e-104">Within the .NET Framework, you can create DiffGrams and use them to modify data in tables in a Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3fb7e-105">이 섹션에서는 DiffGram을 간략하게 소개하고 DiffGram 사용 방법의 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3fb7e-105">This section provides a brief introduction to DiffGrams and examples of how to use them.</span></span> <span data-ttu-id="3fb7e-106">사용자가 .NET Framework의 DiffGram에 대해 잘 알고 있다고 가정합니다.</span><span class="sxs-lookup"><span data-stu-id="3fb7e-106">It is assumed that you are familiar with DiffGrams in the .NET Framework.</span></span> <span data-ttu-id="3fb7e-107">이 설명서에서는 SQLXML과 관련된 DiffGram 문제를 중점적으로 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="3fb7e-107">In this documentation, the primary focus is on DiffGram issues that are specific to SQLXML.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3fb7e-108">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="3fb7e-108">In This Section</span></span>  
 [<span data-ttu-id="3fb7e-109">SQLXML 4.0의 DiffGrams 소개</span><span class="sxs-lookup"><span data-stu-id="3fb7e-109">Introduction to DiffGrams in SQLXML 4.0</span></span>](introduction-to-diffgrams-in-sqlxml-4-0.md)  
 <span data-ttu-id="3fb7e-110">Diffgram에 대한 기본 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3fb7e-110">Provides basic information about Diffgrams.</span></span>  
  
 [<span data-ttu-id="3fb7e-111">DiffGram 예 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="3fb7e-111">DiffGram Examples &#40;SQLXML 4.0&#41;</span></span>](diffgram-examples-sqlxml-4-0.md)  
 <span data-ttu-id="3fb7e-112">Diffgram 사용 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3fb7e-112">Provides examples of using Diffgrams.</span></span>  
  
 [<span data-ttu-id="3fb7e-113">&#40;SQLXML 4.0&#41;ADO를 사용 하 여 DiffGram 실행</span><span class="sxs-lookup"><span data-stu-id="3fb7e-113">Executing a DiffGram by Using ADO &#40;SQLXML 4.0&#41;</span></span>](executing-a-diffgram-by-using-ado-sqlxml-4-0.md)  
 <span data-ttu-id="3fb7e-114">ADO(ActiveX Data Objects)를 사용하여 Diffgram을 실행하는 방법의 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3fb7e-114">Provides an example of executing a Diffgram with ActiveX Data Objects (ADO).</span></span>  
  
 [<span data-ttu-id="3fb7e-115">SQLXML 관리되는 클래스를 사용하여 DiffGram 실행</span><span class="sxs-lookup"><span data-stu-id="3fb7e-115">Executing a DiffGram by Using SQLXML Managed Classes</span></span>](../net-framework-classes/sqlxml-4-0-net-framework-support-managed-classes.md)  
 <span data-ttu-id="3fb7e-116">SQLXML 관리되는 클래스를 사용하여 Diffgram을 실행하는 방법의 예를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="3fb7e-116">Provides an example of executing a Diffgram with SQLXML Managed Classes.</span></span>  
  
  
