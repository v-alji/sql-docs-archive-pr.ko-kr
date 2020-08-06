---
title: 백업 디바이스 선택 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.selectbackupdevice.f1
ms.assetid: 7887c9fd-15ce-4cc8-b069-845c1d09088c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a848f9188eec0ebb09931bca460b0389b9570ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736418"
---
# <a name="select-backup-device"></a><span data-ttu-id="bb8bd-102">백업 디바이스 선택</span><span class="sxs-lookup"><span data-stu-id="bb8bd-102">Select Backup Device</span></span>
  <span data-ttu-id="bb8bd-103">**백업 디바이스 선택** 대화 상자를 사용하여 복원 작업에 사용할 논리적 백업 디바이스를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8bd-103">Use the **Select Backup Device** dialog box to select a logical backup device for the restore operation.</span></span>  
  
 <span data-ttu-id="bb8bd-104">논리적 백업 디바이스는 운영 체제가 제공하는 물리적 디바이스인 테이프 드라이브 또는 디스크 드라이브에 해당하는 사용자 정의된 논리적 디바이스입니다.</span><span class="sxs-lookup"><span data-stu-id="bb8bd-104">A logical backup device is a user-defined logical device that corresponds to a physical device, either a tape drive or a disk drive, that is provided by the operating system.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bb8bd-105">백업에 여러 개의 백업 디바이스가 사용될 경우 이러한 디바이스는 하나로 일치해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8bd-105">If a backup uses multiple backup devices, they all must correspond to a single type of device.</span></span>  
  
 <span data-ttu-id="bb8bd-106">**SQL Server Management Studio를 사용하여 백업 디바이스의 내용을 보려면**</span><span class="sxs-lookup"><span data-stu-id="bb8bd-106">**To use SQL Server Management Studio to view the contents of a backup device**</span></span>  
  
-   [<span data-ttu-id="bb8bd-107">백업 테이프 또는 파일의 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bb8bd-107">View the Contents of a Backup Tape or File &#40;SQL Server&#41;</span></span>](view-the-contents-of-a-backup-tape-or-file-sql-server.md)  
  
-   [<span data-ttu-id="bb8bd-108">논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bb8bd-108">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
## <a name="options"></a><span data-ttu-id="bb8bd-109">옵션</span><span class="sxs-lookup"><span data-stu-id="bb8bd-109">Options</span></span>  
 <span data-ttu-id="bb8bd-110">**백업 디바이스**</span><span class="sxs-lookup"><span data-stu-id="bb8bd-110">**Backup device**</span></span>  
 <span data-ttu-id="bb8bd-111">목록 상자에서 복원할 논리적 백업 디바이스의 이름을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8bd-111">In the list box, select the name of a logical backup device from which you want to restore.</span></span>  
  
 <span data-ttu-id="bb8bd-112">백업 디바이스의 내용을 보는 방법은 [논리적 백업 디바이스의 속성 및 내용 보기&#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="bb8bd-112">For information about how to view the contents of a backup device, see [View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb8bd-113">설명</span><span class="sxs-lookup"><span data-stu-id="bb8bd-113">Remarks</span></span>  
 <span data-ttu-id="bb8bd-114">목록에서 찾고 있는 백업이 포함된 논리적 백업 디바이스가 보이지 않을 경우 백업은 하나 이상의 파일 또는 테이프 드라이브에 직접 기록되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="bb8bd-114">If you do not see a logical backup device that contains the backup you are seeking on the list, the backup might have been written directly to one or more files or tape drives.</span></span> <span data-ttu-id="bb8bd-115">이 경우에는 **백업 디바이스 선택** 대화 상자를 취소하고 **백업 지정** 대화 상자의 **백업 미디어** 목록 상자에서 **파일** 또는 **테이프** 를 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="bb8bd-115">If this is the case, cancel the **Select Backup Device** dialog box; and in the **Specify Backup** dialog box, select **File** or **Tape** in the **Backup media** list box.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb8bd-116">참고 항목</span><span class="sxs-lookup"><span data-stu-id="bb8bd-116">See Also</span></span>  
 [<span data-ttu-id="bb8bd-117">백업 디바이스&#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="bb8bd-117">Backup Devices &#40;SQL Server&#41;</span></span>](backup-devices-sql-server.md)  
  
  
