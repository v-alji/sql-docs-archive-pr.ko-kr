---
title: MSSQLSERVER_9524 | Microsoft 문서
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e6c46ee0ef0bd1be299614e2cb04a3d6cd99d92e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650034"
---
# <a name="mssqlserver_9524"></a><span data-ttu-id="d7510-102">MSSQLSERVER_9524</span><span class="sxs-lookup"><span data-stu-id="d7510-102">MSSQLSERVER_9524</span></span>
    
## <a name="details"></a><span data-ttu-id="d7510-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="d7510-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d7510-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="d7510-104">Product Name</span></span>|<span data-ttu-id="d7510-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d7510-105">SQL Server</span></span>|  
|<span data-ttu-id="d7510-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="d7510-106">Event ID</span></span>|<span data-ttu-id="d7510-107">9254</span><span class="sxs-lookup"><span data-stu-id="d7510-107">9254</span></span>|  
|<span data-ttu-id="d7510-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="d7510-108">Event Source</span></span>|<span data-ttu-id="d7510-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d7510-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d7510-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="d7510-110">Component</span></span>|<span data-ttu-id="d7510-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d7510-111">SQLEngine</span></span>|  
|<span data-ttu-id="d7510-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="d7510-112">Symbolic Name</span></span>|<span data-ttu-id="d7510-113">XMLERR_INVALID_COLUMNSET_XML</span><span class="sxs-lookup"><span data-stu-id="d7510-113">XMLERR_INVALID_COLUMNSET_XML</span></span>|  
|<span data-ttu-id="d7510-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="d7510-114">Message Text</span></span>|<span data-ttu-id="d7510-115">제공한 XML 내용이 스파스 열 집합의 필수 XML 형식에 맞지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="d7510-115">The XML content provided does not conform to the required XML format for sparse column sets.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d7510-116">설명</span><span class="sxs-lookup"><span data-stu-id="d7510-116">Explanation</span></span>  
 <span data-ttu-id="d7510-117">열 집합을 수정하려고 했습니다.</span><span class="sxs-lookup"><span data-stu-id="d7510-117">An attempt was made to modify a column set.</span></span> <span data-ttu-id="d7510-118">열 집합의 XML 내용은 열 집합의 형식 제한 사항을 충족해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d7510-118">The XML content of a column set must meet the format restrictions of a column set.</span></span> <span data-ttu-id="d7510-119">일반 열 집합 형식은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d7510-119">The general format of a column set is as follows:</span></span>  
  
 `<column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...`  
  
 <span data-ttu-id="d7510-120">열 집합에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 온라인 설명서의 "열 집합 사용" 항목을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d7510-120">For more information about column sets, see the topic "Using Column Sets" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d7510-121">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="d7510-121">User Action</span></span>  
 <span data-ttu-id="d7510-122">문에 포함된 열 집합의 XML 형식을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="d7510-122">Correct the format of the XML for the column set in the statement.</span></span>  
  
  
