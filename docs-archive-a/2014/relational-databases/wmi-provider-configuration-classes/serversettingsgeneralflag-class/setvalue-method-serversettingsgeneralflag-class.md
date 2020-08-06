---
title: SetValue 메서드 (ServerSettingsGeneralFlag 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetValue Method (ServerSettingsGeneralFlag Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetValue method
ms.assetid: a889feac-c0e0-4635-b506-843863d86967
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 74c4c189b72b7a469794e0828faf062a88cdf46f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743128"
---
# <a name="setvalue-method-serversettingsgeneralflag-class"></a><span data-ttu-id="0a117-102">SetValue 메서드(ServerSettingsGeneralFlag 클래스)</span><span class="sxs-lookup"><span data-stu-id="0a117-102">SetValue Method (ServerSettingsGeneralFlag Class)</span></span>
  <span data-ttu-id="0a117-103">참조된 플래그의 모든 값을 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="0a117-103">Sets all the values of the referenced flag.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a117-104">구문</span><span class="sxs-lookup"><span data-stu-id="0a117-104">Syntax</span></span>  
  
```  
  
object  
.SetValue(  
Value  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="0a117-105">부분</span><span class="sxs-lookup"><span data-stu-id="0a117-105">Parts</span></span>  
 <span data-ttu-id="0a117-106">*object*</span><span class="sxs-lookup"><span data-stu-id="0a117-106">*object*</span></span>  
 <span data-ttu-id="0a117-107">서버 설정에 대한 일반 플래그를 나타내는 [ServerSettingsGeneralFlag 클래스](serversettingsgeneralflag-class.md) 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="0a117-107">A [ServerSettingsGeneralFlag Class](serversettingsgeneralflag-class.md) object that represents a general flag for the server settings.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="0a117-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a117-108">Parameters</span></span>  
  
|<span data-ttu-id="0a117-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="0a117-109">Parameter</span></span>|<span data-ttu-id="0a117-110">설명</span><span class="sxs-lookup"><span data-stu-id="0a117-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a117-111">*값*</span><span class="sxs-lookup"><span data-stu-id="0a117-111">*Value*</span></span>|<span data-ttu-id="0a117-112">플래그의 값을 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="0a117-112">A Boolean value that specifies the value of the flag.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="0a117-113">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="0a117-113">Property Value/Return Value</span></span>  
 <span data-ttu-id="0a117-114">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0a117-114">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a117-115">설명</span><span class="sxs-lookup"><span data-stu-id="0a117-115">Remarks</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a117-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="0a117-116">See Also</span></span>  
 <span data-ttu-id="0a117-117">[서버 네트워크 프로토콜 및 네트워크 라이브러리 구성](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span><span class="sxs-lookup"><span data-stu-id="0a117-117">[Configuring Server Network Protocols and Net-Libraries](https://msdn.microsoft.com/library/ms177485\(v=sql.100\).aspx)</span></span>  
  
  
