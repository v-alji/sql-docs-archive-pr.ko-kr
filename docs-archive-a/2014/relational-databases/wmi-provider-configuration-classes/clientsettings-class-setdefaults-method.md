---
title: SetDefaults 메서드 (ClientSettings 클래스) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- SetDefaults Method (ClientSettings Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- SetDefaults method
ms.assetid: 056508f3-a5c8-467c-a196-dc1ef1f5178f
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: b6985ebfa4a9145dd3474cec31f32cdab9c11cdc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660362"
---
# <a name="setdefaults-method-clientsettings-class"></a><span data-ttu-id="dfb2d-102">SetDefaults 메서드(ClientSettings 클래스)</span><span class="sxs-lookup"><span data-stu-id="dfb2d-102">SetDefaults Method (ClientSettings Class)</span></span>
  <span data-ttu-id="dfb2d-103">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기존 데이터를 덮어쓰는 옵션을 사용 하 여 클라이언트 인스턴스에 대 한 모든 기본값을 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-103">Sets all the default values for the instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client with the option to overwrite existing data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfb2d-104">구문</span><span class="sxs-lookup"><span data-stu-id="dfb2d-104">Syntax</span></span>  
  
```  
  
object  
.SetDefaults(  
OverwriteAll  
)  
  
```  
  
## <a name="parts"></a><span data-ttu-id="dfb2d-105">부분</span><span class="sxs-lookup"><span data-stu-id="dfb2d-105">Parts</span></span>  
 <span data-ttu-id="dfb2d-106">*object*</span><span class="sxs-lookup"><span data-stu-id="dfb2d-106">*object*</span></span>  
 <span data-ttu-id="dfb2d-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트 인스턴스를 나타내는 `ClientSettings` 개체입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-107">A `ClientSettings` object that represents a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client instance.</span></span>  
  
#### <a name="parameters"></a><span data-ttu-id="dfb2d-108">매개 변수</span><span class="sxs-lookup"><span data-stu-id="dfb2d-108">Parameters</span></span>  
  
|<span data-ttu-id="dfb2d-109">매개 변수</span><span class="sxs-lookup"><span data-stu-id="dfb2d-109">Parameter</span></span>|<span data-ttu-id="dfb2d-110">Description</span><span class="sxs-lookup"><span data-stu-id="dfb2d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dfb2d-111">*OverwriteAll*</span><span class="sxs-lookup"><span data-stu-id="dfb2d-111">*OverwriteAll*</span></span>|<span data-ttu-id="dfb2d-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 클라이언트 인스턴스의 기존 값을 덮어쓸지 여부를 지정하는 부울 값입니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-112">A Boolean value that specifies whether to overwrite existing values on the instance of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] client.</span></span> <span data-ttu-id="dfb2d-113">`true`인 경우 기존 데이터를 덮어쓰고 `false`인 경우 기존 데이터를 덮어쓰지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-113">`true` to overwrite existing data; `false` if existing data is not to be overwritten.</span></span>|  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="dfb2d-114">속성 값/반환 값</span><span class="sxs-lookup"><span data-stu-id="dfb2d-114">Property Value/Return Value</span></span>  
 <span data-ttu-id="dfb2d-115">`uint32` 값으로, 0은 서비스가 수정되었음을 나타내고 1은 요청이 지원되지 않음을 나타내며 다른 모든 숫자는 오류를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="dfb2d-115">A `uint32` value, which is 0 if the service was successfully modified, 1 if the request is not supported, and any other number to indicate an error.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfb2d-116">설명</span><span class="sxs-lookup"><span data-stu-id="dfb2d-116">Remarks</span></span>  
  
