---
title: PAGE_VERIFY 데이터베이스 옵션을 CHECKSUM으로 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 686b9a4a-ea61-4263-9ab8-f444a3077679
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 13296a976722390668b8ca6d901cf0dd080e5cc3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740836"
---
# <a name="set-the-page_verify-database-option-to-checksum"></a><span data-ttu-id="18cfd-102">PAGE_VERIFY 데이터베이스 옵션을 CHECKSUM으로 설정</span><span class="sxs-lookup"><span data-stu-id="18cfd-102">Set the PAGE_VERIFY Database Option to CHECKSUM</span></span>
  <span data-ttu-id="18cfd-103">이 규칙은 PAGE_VERIFY 데이터베이스 옵션이 CHECKSUM으로 설정되었는지 검사합니다.</span><span class="sxs-lookup"><span data-stu-id="18cfd-103">This rule checks whether PAGE_VERIFY database option is set to CHECKSUM.</span></span> <span data-ttu-id="18cfd-104">PAGE_VERIFY 데이터베이스 옵션에 CHECKSUM을 설정하면 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 에서 페이지를 디스크에 쓸 때 전체 페이지 내용에 대한 체크섬이 계산되어 페이지 헤더에 값이 저장됩니다.</span><span class="sxs-lookup"><span data-stu-id="18cfd-104">When CHECKSUM is enabled for the PAGE_VERIFY database option, the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] calculates a checksum over the contents of the whole page, and stores the value in the page header when a page is written to disk.</span></span> <span data-ttu-id="18cfd-105">디스크에서 페이지를 읽으면 체크섬이 다시 계산되어 페이지 헤더에 저장된 체크섬 값과 비교됩니다.</span><span class="sxs-lookup"><span data-stu-id="18cfd-105">When the page is read from disk, the checksum is recomputed and compared to the checksum value that is stored in the page header.</span></span> <span data-ttu-id="18cfd-106">이를 통해 높은 수준의 데이터 파일 무결성을 제공할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="18cfd-106">This helps provide a high level of data-file integrity.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="18cfd-107">최선의 구현 방법 권장 사항</span><span class="sxs-lookup"><span data-stu-id="18cfd-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="18cfd-108">PAGE_VERIFY 데이터베이스 옵션을 CHECKSUM으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="18cfd-108">Set the PAGE_VERIFY database option to CHECKSUM.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="18cfd-109">참조 항목</span><span class="sxs-lookup"><span data-stu-id="18cfd-109">For More Information</span></span>  
 [<span data-ttu-id="18cfd-110">ALTER DATABASE SET 옵션&#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="18cfd-110">ALTER DATABASE SET Options &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-database-transact-sql-set-options)  
  
  
