---
title: SqlToolsVSNativeHelpers | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: d33cb556-0380-490a-9220-b74062dbd6d9
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 84f8a3a3408b68cb8c389b05b417f391a1f86c93
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743132"
---
# <a name="sqltoolsvsnativehelpers"></a><span data-ttu-id="e9dbe-102">SqlToolsVSNativeHelpers</span><span class="sxs-lookup"><span data-stu-id="e9dbe-102">SqlToolsVSNativeHelpers</span></span>
  <span data-ttu-id="e9dbe-103">Visual Studio에서 SQL Server 기능을 지원하는 라이브러리입니다.</span><span class="sxs-lookup"><span data-stu-id="e9dbe-103">Library that supports SQL Server functionality in Visual Studio.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9dbe-104">구문</span><span class="sxs-lookup"><span data-stu-id="e9dbe-104">Syntax</span></span>  
  
```  
  
BOOL WINAPI DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID /*lpReserved*/)  
```  
  
## <a name="return-value"></a><span data-ttu-id="e9dbe-105">Return Value</span><span class="sxs-lookup"><span data-stu-id="e9dbe-105">Return Value</span></span>  
 <span data-ttu-id="e9dbe-106">DLL 진입점이 올바르게 초기화된 경우 부울 값 `True`이고, 그렇지 않으면 `False`입니다.</span><span class="sxs-lookup"><span data-stu-id="e9dbe-106">A Boolean value, `True` if the DLL entry point initialized properly, otherwise `False`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9dbe-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="e9dbe-107">See Also</span></span>  
 [<span data-ttu-id="e9dbe-108">FrameWindowVisible</span><span class="sxs-lookup"><span data-stu-id="e9dbe-108">FrameWindowVisible</span></span>](sqltoolsvsnativehelpers-framewindowvisible.md)  
  
  
