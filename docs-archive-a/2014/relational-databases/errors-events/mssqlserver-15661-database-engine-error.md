---
title: MSSQLSERVER_15661 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 966e23e8d970c36eba81253228cc18ed4af3ff77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638814"
---
# <a name="mssqlserver_15661"></a><span data-ttu-id="5c198-102">MSSQLSERVER_15661</span><span class="sxs-lookup"><span data-stu-id="5c198-102">MSSQLSERVER_15661</span></span>
    
## <a name="details"></a><span data-ttu-id="5c198-103">세부 정보</span><span class="sxs-lookup"><span data-stu-id="5c198-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5c198-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="5c198-104">Product Name</span></span>|<span data-ttu-id="5c198-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="5c198-105">SQL Server</span></span>|  
|<span data-ttu-id="5c198-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="5c198-106">Event ID</span></span>|<span data-ttu-id="5c198-107">15661</span><span class="sxs-lookup"><span data-stu-id="5c198-107">15661</span></span>|  
|<span data-ttu-id="5c198-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="5c198-108">Event Source</span></span>|<span data-ttu-id="5c198-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="5c198-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="5c198-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="5c198-110">Component</span></span>|<span data-ttu-id="5c198-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="5c198-111">SQLEngine</span></span>|  
|<span data-ttu-id="5c198-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="5c198-112">Symbolic Name</span></span>|<span data-ttu-id="5c198-113">SQLErrorNum15661</span><span class="sxs-lookup"><span data-stu-id="5c198-113">SQLErrorNum15661</span></span>|  
|<span data-ttu-id="5c198-114">메시지 텍스트</span><span class="sxs-lookup"><span data-stu-id="5c198-114">Message Text</span></span>|<span data-ttu-id="5c198-115">sp_estimate_data_compression_savings 저장 프로시저는 임시 테이블로 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5c198-115">The sp_estimate_data_compression_savings stored procedure cannot be used for temporary tables.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5c198-116">설명</span><span class="sxs-lookup"><span data-stu-id="5c198-116">Explanation</span></span>  
 <span data-ttu-id="5c198-117">임시 테이블이 sp_estimate_data_compression_savings 저장 프로시저의 인수로 사용되었습니다.</span><span class="sxs-lookup"><span data-stu-id="5c198-117">A temporary table was used as an argument for the sp_estimate_data_compression_savings stored procedure.</span></span> <span data-ttu-id="5c198-118">임시 테이블을 압축할 수는 있지만 sp_estimate_data_compression_savings를 사용하여 압축 전후 크기 변경 사항을 예상할 수는 없습니다.</span><span class="sxs-lookup"><span data-stu-id="5c198-118">Although the compression of temporary tables is supported, you cannot use sp_estimate_data_compression_savings to estimate the compression savings.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5c198-119">사용자 동작</span><span class="sxs-lookup"><span data-stu-id="5c198-119">User Action</span></span>  
 <span data-ttu-id="5c198-120">sp_estimate_data_compression_savings의 인수로 사용된 임시 테이블을 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="5c198-120">Remove the temporary table as an argument for sp_estimate_data_compression_savings.</span></span>  
  
  
