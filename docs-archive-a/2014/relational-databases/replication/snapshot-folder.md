---
title: 스냅샷 폴더 | Microsoft 문서
ms.custom: ''
ms.date: 06/30/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.replicationutilities.specifysnapshotfolder.f1
ms.assetid: 3eb1b73f-ddb3-4d09-be6e-811c414698e9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 48b490c65662edf65018e98dd1bc3339f6aae6b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661003"
---
# <a name="snapshot-folder"></a><span data-ttu-id="9754a-102">스냅샷 폴더</span><span class="sxs-lookup"><span data-stu-id="9754a-102">Snapshot Folder</span></span>
  <span data-ttu-id="9754a-103">**스냅샷 폴더** 페이지는 배포 구성 마법사 및 새 게시 마법사에 나타납니다.</span><span class="sxs-lookup"><span data-stu-id="9754a-103">The **Snapshot Folder** page appears in the Configure Distribution Wizard and in the New Publication Wizard.</span></span> <span data-ttu-id="9754a-104">지정하는 스냅샷 폴더 위치는 이 마법사에서 설정하는 모든 게시자의 기본값으로 사용됩니다. 기본 스냅샷 폴더는 나중에 **배포자 속성** 대화 상자를 사용하여 설정하는 게시자에는 적용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9754a-104">The location you specify for the snapshot folder will be used as the default for all Publishers enabled in this wizard (the default snapshot folder does not apply to Publishers that are later enabled using the **Distributor Properties** dialog box).</span></span> <span data-ttu-id="9754a-105">배포 구성 마법사 또는 **배포자 속성** 대화 상자의 **게시자** 페이지에서 임의의 게시자에 대해 이 기본값을 무시할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9754a-105">You can override this default for any Publisher on the **Publishers** page of the Configure Distribution Wizard or the **Distributor Properties** dialog box.</span></span>  
  
 <span data-ttu-id="9754a-106">스냅샷 폴더는 공유하도록 지정된 디렉터리일 뿐이며 이 폴더에 읽기/쓰기 작업을 수행하려면 에이전트에게 충분한 액세스 권한이 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9754a-106">The snapshot folder is simply a directory that you have designated as a share; agents that read from and write to this folder must have sufficient permissions to access it.</span></span> <span data-ttu-id="9754a-107">폴더의 적절한 보안 유지 방법에 대한 자세한 내용은 [스냅샷 폴더 보안 설정](security/secure-the-snapshot-folder.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9754a-107">For more information about securing the folder appropriately, see [Secure the Snapshot Folder](security/secure-the-snapshot-folder.md).</span></span> <span data-ttu-id="9754a-108">복제를 구현하기 전에 복제 에이전트에서 스냅샷 폴더에 연결할 수 있는지 테스트합니다.</span><span class="sxs-lookup"><span data-stu-id="9754a-108">Prior to implementing replication, test that the replication agents will be able to connect to the snapshot folder.</span></span> <span data-ttu-id="9754a-109">각 에이전트에서 사용할 계정으로 로그온한 다음 스냅샷 폴더에 액세스해 봅니다.</span><span class="sxs-lookup"><span data-stu-id="9754a-109">Log on under the account that will be used by each agent and then attempt to access the snapshot folder.</span></span>  
  
## <a name="options"></a><span data-ttu-id="9754a-110">옵션</span><span class="sxs-lookup"><span data-stu-id="9754a-110">Options</span></span>  
 <span data-ttu-id="9754a-111">**스냅샷 폴더**</span><span class="sxs-lookup"><span data-stu-id="9754a-111">**Snapshot folder**</span></span>  
 <span data-ttu-id="9754a-112">스냅샷 파일을 저장할 폴더의 경로를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="9754a-112">Enter the path for the folder where you want snapshot files stored.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="9754a-113">은(는) 네트워크 공유를 스냅샷 폴더 위치로 사용하는 것을 권장합니다.</span><span class="sxs-lookup"><span data-stu-id="9754a-113">recommends that you use a network share as a snapshot folder location.</span></span> <span data-ttu-id="9754a-114">다른 컴퓨터의 에이전트는 로컬 경로(C:\\와 같이 드라이브 문자로 시작하는 경로)에 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9754a-114">Local paths (those starting with a drive letter, such as C:\\) are not accessible to agents on other computers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9754a-115">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9754a-115">See Also</span></span>  
 <span data-ttu-id="9754a-116">[대체 스냅숏 폴더 위치](alternate-snapshot-folder-locations.md) </span><span class="sxs-lookup"><span data-stu-id="9754a-116">[Alternate Snapshot Folder Locations](alternate-snapshot-folder-locations.md) </span></span>  
 <span data-ttu-id="9754a-117">[배포 구성](configure-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="9754a-117">[Configure Distribution](configure-distribution.md) </span></span>  
 <span data-ttu-id="9754a-118">[게시 및 배포 구성](configure-publishing-and-distribution.md) </span><span class="sxs-lookup"><span data-stu-id="9754a-118">[Configure Publishing and Distribution](configure-publishing-and-distribution.md) </span></span>  
 <span data-ttu-id="9754a-119">[배포자 및 게시자 속성 보기 및 수정](view-and-modify-distributor-and-publisher-properties.md) </span><span class="sxs-lookup"><span data-stu-id="9754a-119">[View and Modify Distributor and Publisher Properties](view-and-modify-distributor-and-publisher-properties.md) </span></span>  
 [<span data-ttu-id="9754a-120">스냅샷으로 구독 초기화</span><span class="sxs-lookup"><span data-stu-id="9754a-120">Initialize a Subscription with a Snapshot</span></span>](initialize-a-subscription-with-a-snapshot.md)  
  
  
