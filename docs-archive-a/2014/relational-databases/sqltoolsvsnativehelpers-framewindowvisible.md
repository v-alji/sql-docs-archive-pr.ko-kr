---
title: FrameWindowVisible | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 9091d714-98bc-43ec-b8d1-9c892cb57f19
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 414f1a03ea87f6cc6b0916a0122ca2a66d5855a2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743136"
---
# <a name="framewindowvisible"></a><span data-ttu-id="26ce7-102">FrameWindowVisible</span><span class="sxs-lookup"><span data-stu-id="26ce7-102">FrameWindowVisible</span></span>
  <span data-ttu-id="26ce7-103">지정된 창 프레임이 표시되는지 여부를 지정하는 속성입니다.</span><span class="sxs-lookup"><span data-stu-id="26ce7-103">Property that specifies whether a given window frame is visible.</span></span> <span data-ttu-id="26ce7-104">도우미 메서드는 관리 코드에서 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="26ce7-104">The helper method is used from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26ce7-105">구문</span><span class="sxs-lookup"><span data-stu-id="26ce7-105">Syntax</span></span>  
  
```  
  
BOOL WINAPI IsFrameWindowVisible(IVsWindowFrame* frame)  
{  
    if (NULL == frame)  
    {  
        return FALSE;  
    }  
  
    return S_OK == frame->IsVisible();  
}  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26ce7-106">매개 변수</span><span class="sxs-lookup"><span data-stu-id="26ce7-106">Parameters</span></span>  
 <span data-ttu-id="26ce7-107">*frame*</span><span class="sxs-lookup"><span data-stu-id="26ce7-107">*frame*</span></span>  
  
 <span data-ttu-id="26ce7-108">Visual Studio WindowFrame에 대한 IVsWindowFrame\* 포인터입니다.</span><span class="sxs-lookup"><span data-stu-id="26ce7-108">IVsWindowFrame\* pointer to a Visual Studio WindowFrame.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="26ce7-109">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="26ce7-109">Property Value/Return Value</span></span>  
 <span data-ttu-id="26ce7-110">*frame* 으로 지정된 창 프레임이 표시되는지 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="26ce7-110">A Boolean value that specifies whether the window frame specified by *frame* is visible.</span></span>  
  

<!-- Necessary temporarily. GeneMi, 2018-05-01.
     But 'release-sql2014-migration' should win the Conflict Resolution later in May, because this will then be a good link!
## See Also  
 [SqlToolsVSNativeHelpers](sqltoolsvsnativehelpers.md)  
-->
  
  
