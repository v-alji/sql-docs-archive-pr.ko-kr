---
title: 오류 처리 (MDX) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- scripts [MDX], exceptions
- exceptions [MDX]
ms.assetid: bc6ff0af-9fe6-44d6-bc3c-801d71ea41a9
author: minewiskan
ms.author: owend
ms.openlocfilehash: 357194b9f789fdeacfb65ce3c894d4747867eafb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87653614"
---
# <a name="error-handling-mdx"></a><span data-ttu-id="bc8e1-102">오류 처리(MDX)</span><span class="sxs-lookup"><span data-stu-id="bc8e1-102">Error Handling (MDX)</span></span>
  <span data-ttu-id="bc8e1-103">MDX 스크립트의 오류가 처리되는 방법을 각 큐브에서 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bc8e1-103">Each cube can control how errors within a Multidimensional Expressions (MDX) script are handled.</span></span> <span data-ttu-id="bc8e1-104">오류 처리는 `ScriptErrorHandlingMode` 열거자를 통해 수행됩니다.</span><span class="sxs-lookup"><span data-stu-id="bc8e1-104">Error handling is done through the `ScriptErrorHandlingMode` enumerator.</span></span> <span data-ttu-id="bc8e1-105">이 열거자에 사용할 수 있는 값은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="bc8e1-105">The possible values for this enumerator are:</span></span>  
  
 `IgnoreNone`  
 <span data-ttu-id="bc8e1-106">가 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] MDX 스크립트에서 오류를 발견 하면 서버에서 오류를 발생 시킵니다.</span><span class="sxs-lookup"><span data-stu-id="bc8e1-106">Causes the server to raise an error when [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] finds any error in the MDX script.</span></span>  
  
 `IgnoreAll`  
 <span data-ttu-id="bc8e1-107">구문 오류, 이름 확인 오류 등을 포함하는 MDX 스크립트 내의 모든 명령을 서버가 무시하도록 합니다.</span><span class="sxs-lookup"><span data-stu-id="bc8e1-107">Causes the server to ignore all commands in the MDX script that contain an error, including syntax errors, name resolution errors, and more.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc8e1-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bc8e1-108">See Also</span></span>  
 <xref:Microsoft.AnalysisServices.Cube.ScriptErrorHandlingMode%2A>  
  
  
