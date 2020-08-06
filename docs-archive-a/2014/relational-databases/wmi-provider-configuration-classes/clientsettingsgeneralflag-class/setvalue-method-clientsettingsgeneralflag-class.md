---
title: SetValue 메서드 (ClientSettingsGeneralFlag 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetValue Method (ClientSettingsGeneralFlag Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetValue method
ms.assetid: 34443689-a0e0-4668-a811-17532c6fd271
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: fffa44bd8743f96a43ca4d1787d8d2afaad5e6cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87729300"
---
# <a name="setvalue-method-clientsettingsgeneralflag-class"></a><span data-ttu-id="37b2d-102">SetValue 메서드(ClientSettingsGeneralFlag 클래스)</span><span class="sxs-lookup"><span data-stu-id="37b2d-102">SetValue Method (ClientSettingsGeneralFlag Class)</span></span>
  <span data-ttu-id="37b2d-103">참조된 플래그의 모든 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="37b2d-103">Sets all the values of the referenced flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37b2d-104">구문</span><span class="sxs-lookup"><span data-stu-id="37b2d-104">Syntax</span></span>  
  
```  
  
object  
.SetValue(  
Value  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="37b2d-105">부분</span><span class="sxs-lookup"><span data-stu-id="37b2d-105">Parts</span></span>  
 <span data-ttu-id="37b2d-106">*object*</span><span class="sxs-lookup"><span data-stu-id="37b2d-106">*object*</span></span>  
 <span data-ttu-id="37b2d-107">서버 설정에 대한 일반 플래그를 나타내는 [ClientSettingsGeneralFlag 클래스](clientsettingsgeneralflag-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="37b2d-107">A [ClientSettingsGeneralFlag Class](clientsettingsgeneralflag-class.md) object that represents a general flag for the server settings.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="37b2d-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="37b2d-108">Parameters</span></span>  
  
|<span data-ttu-id="37b2d-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="37b2d-109">Parameter</span></span>|<span data-ttu-id="37b2d-110">Description</span><span class="sxs-lookup"><span data-stu-id="37b2d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37b2d-111">*값*</span><span class="sxs-lookup"><span data-stu-id="37b2d-111">*Value*</span></span>|<span data-ttu-id="37b2d-112">플래그의 값을 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="37b2d-112">A Boolean value that specifies the value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="37b2d-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="37b2d-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="37b2d-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="37b2d-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="37b2d-115">설명</span><span class="sxs-lookup"><span data-stu-id="37b2d-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37b2d-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="37b2d-116">See Also</span></span>  
 [<span data-ttu-id="37b2d-117">클라이언트 프로토콜 구성</span><span class="sxs-lookup"><span data-stu-id="37b2d-117">Configure Client Protocols</span></span>](https://technet.microsoft.com/library/ms181035.aspx)  
  
  
